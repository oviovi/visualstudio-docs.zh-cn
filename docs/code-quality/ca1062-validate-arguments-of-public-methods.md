---
title: CA1062:验证公共方法的参数
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1b3b9461c72b21fcb2b77590786f47b90f5a98f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860749"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062:验证公共方法的参数

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|类别|Microsoft.Design|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

外部可见方法取消引用一个引用参数而不验证该参数是否`null`(`Nothing`在 Visual Basic 中)。

## <a name="rule-description"></a>规则说明

应根据检查传递给外部可见方法的所有引用参数`null`。 如果适用，引发<xref:System.ArgumentNullException>时，参数是`null`。

如果可以从未知的程序集调用的方法，因为它被声明为公共或受保护，则应验证所有参数的方法。 如果该方法旨在只能由已知程序集调用，应使该方法内部，并应用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性为包含该方法的程序集。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复此规则的冲突，请验证每个引用参数是否为`null`。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

是否确实已通过在函数中的另一个方法调用验证的取消引用的参数，可以禁止显示此规则的警告。

## <a name="example"></a>示例

下面的示例演示与规则冲突的方法和满足该规则的方法。

 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>示例

填充字段或所引用对象的属性的复制构造函数还可以违反 CA1062 规则。 复制到复制构造函数传递的对象可能是因为发生了冲突`null`(`Nothing`在 Visual Basic 中)。 若要解决冲突，请使用静态 (在 Visual Basic 中的为 Shared) 方法来检查复制的对象不为 null。

在下面的示例`Person`类的示例中，`other`对象传递给`Person`复制构造函数可能是`null`。

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>示例

在下面进行了修订`Person`示例中，`other`对象传递给复制构造函数将首先检查中的 null`PassThroughNonNull`方法。

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```