---
title: CA2220:终结器应调用基类的终结器
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4befae0ca3095994c3d48d20647045d4825154e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825391"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220:终结器应调用基类的终结器

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

重写的类型<xref:System.Object.Finalize%2A?displayProperty=fullName>不会调用<xref:System.Object.Finalize%2A>中其基本类的方法。

## <a name="rule-description"></a>规则说明

终止必须通过继承层次结构传播。 若要确保这一点，类型必须调用其基类<xref:System.Object.Finalize%2A>方法从其自身<xref:System.Object.Finalize%2A>方法。 C# 编译器会自动添加到基类的终结器调用。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复此规则的冲突，请调用基类型<xref:System.Object.Finalize%2A>方法从你<xref:System.Object.Finalize%2A>方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

不禁止显示此规则发出的警告。 面向公共语言运行时的某些编译器对基类型的终结器的调用插入到 Microsoft 中间语言 (MSIL)。 如果报告此规则的警告，则编译器不会插入调用，并必须将其添加到你的代码。

## <a name="example"></a>示例

下面的 Visual Basic 示例显示了一种类型`TypeB`的正确调用<xref:System.Object.Finalize%2A>中其基本类的方法。

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>请参阅

- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)