---
title: CA2218： 重写 Equals 时重写 GetHashCode |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc9e72639e123e0a99c4423b460bc4122995971c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881895"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218：重写 Equals 时重写 GetHashCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因
 公共类型重写<xref:System.Object.Equals%2A?displayProperty=fullName>，但不会重写<xref:System.Object.GetHashCode%2A?displayProperty=fullName>。

## <a name="rule-description"></a>规则说明
 <xref:System.Object.GetHashCode%2A> 返回基于适用于哈希算法和数据结构，例如哈希表的当前实例的值。 属于同一类型且相等的两个对象必须返回相同的哈希代码，以确保以下类型的实例正常工作：

-   <xref:System.Collections.Hashtable?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

-   实现的类型 <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请提供的实现<xref:System.Object.GetHashCode%2A>。 作为一对的相同类型的对象，则必须确保实现返回相同的值，如果你的实现<xref:System.Object.Equals%2A>返回`true`的对。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="class-example"></a>类示例

### <a name="description"></a>描述
 下面的示例演示与此规则冲突的类 （引用类型）。

### <a name="code"></a>代码
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorClass/cs/FxCop.Usage.GetHashCodeErrorClass.cs#1)]

### <a name="comments"></a>注释
 下面的示例通过重写修复了冲突<xref:System.Object.GetHashCode>。

### <a name="code"></a>代码
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass/cs/FxCop.Usage.GetHashCodeFixedClass.cs#1)]

## <a name="structure-example"></a>结构示例

### <a name="description"></a>描述
 下面的示例显示了与此规则冲突的结构 （值类型）。

### <a name="code"></a>代码
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorStruct/cs/FxCop.Usage.GetHashCodeErrorStruct.cs#1)]

### <a name="comments"></a>注释
 下面的示例通过重写修复了冲突<xref:System.Object.GetHashCode>。

### <a name="code"></a>代码
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedStruct/cs/FxCop.Usage.GetHashCodeFixedStruct.cs#1)]

## <a name="related-rules"></a>相关的规则
 [CA1046：不要对引用类型重载相等运算符](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225：运算符重载具有命名的备用项](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226：运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224：重载相等运算符时重写 Equals 方法](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>请参阅

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [相等运算符](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)