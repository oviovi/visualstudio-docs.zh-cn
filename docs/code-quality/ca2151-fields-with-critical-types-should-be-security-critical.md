---
title: CA2151:具有关键类型的字段应为安全关键的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 279e3d134af967467f195f155373bba725b031e0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895215"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151:具有关键类型的字段应为安全关键的

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因

声明了安全透明字段或可靠关键字段。 其类型被指定为安全关键。 例如：

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

在此示例中，`m_field` 是一个安全关键类型的安全透明字段。

## <a name="rule-description"></a>规则说明

若要使用安全关键类型，引用该类型的代码必须是安全关键或安全可靠关键。 即使引用是间接的，也需如此。 例如，当你引用具有关键类型的透明字段时，你的代码必须是安全关键的或安全可靠的。 因此，具有安全透明字段或安全可靠关键字段具有误导性，因为透明代码仍然无法访问该字段。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复此规则的冲突，请将标记与字段<xref:System.Security.SecurityCriticalAttribute>属性，或创建为该类型由字段引用或者安全透明或安全关键。

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

不禁止显示此规则发出的警告。

### <a name="code"></a>代码

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]