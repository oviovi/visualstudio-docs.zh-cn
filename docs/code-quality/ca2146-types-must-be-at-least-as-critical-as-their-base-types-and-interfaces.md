---
title: CA2146:类型必须至少与其基类型和接口一样关键
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 785c31d3d6d58215936e69d0c8034be955c9afd7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899884"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146:类型必须至少与其基类型和接口一样关键

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 透明类型派生自的类型将标有<xref:System.Security.SecuritySafeCriticalAttribute>或<xref:System.Security.SecurityCriticalAttribute>，或类型将标有<xref:System.Security.SecuritySafeCriticalAttribute>特性派生自的类型将标有<xref:System.Security.SecurityCriticalAttribute>属性。

## <a name="rule-description"></a>规则说明
 当派生类型具有的安全透明特性与其基类型或实现的接口不是同样关键时，将引发此规则。 只有关键类型可以从关键基类型派生或实现关键接口，并且只有关键或关键安全类型可以从安全关键基类型派生或实现关键安全接口。 违反此规则在级别 2 透明度导致<xref:System.TypeLoadException>派生的类型。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此冲突，标记是至少为基类型或接口一样关键的透明性属性的派生或实现类型。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]