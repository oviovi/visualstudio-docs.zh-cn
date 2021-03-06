---
title: CA1028:枚举存储应为 Int32
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2d768c5ee98c5bff62dd58c33eb97396088bf978
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868269"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028:枚举存储应为 Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|类别|Microsoft.Design|
|是否重大更改|重大|

## <a name="cause"></a>原因
 公共枚举的基础类型不是<xref:System.Int32?displayProperty=fullName>。

## <a name="rule-description"></a>规则说明
 枚举是一种值类型，它定义一组相关的已命名常数。 默认情况下，<xref:System.Int32?displayProperty=fullName>数据类型用于存储常量值。 即使您可以更改此基础类型，不需要或不建议在大多数情况下。 请注意，通过使用数据类型的最小实现任何显著的性能提升<xref:System.Int32>。 如果您不能使用默认数据类型，则应使用一个公共语言系统 (CLS)-符合整型<xref:System.Byte>， <xref:System.Int16>， <xref:System.Int32>，或<xref:System.Int64>以确保所有枚举值，可以都表示符合 cls 的编程语言。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，除非存在大小或兼容性问题，请使用<xref:System.Int32>。 情况下，<xref:System.Int32>不够大，若要保存的值，请使用<xref:System.Int64>。 如果向后兼容性需要较小的数据类型，请使用<xref:System.Byte>或<xref:System.Int16>。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 仅当需要向后兼容性，禁止显示此规则的警告。 在应用程序中，不符合此规则通常不会导致问题。 在库中，其中语言互操作性是必需的不符合此规则可能产生负面影响你的用户。

## <a name="example-of-a-violation"></a>冲突的示例

### <a name="description"></a>描述
 下面的示例演示两个不使用推荐的基础数据类型的枚举。

### <a name="code"></a>代码
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>修复方法的示例

### <a name="description"></a>描述
 下面的示例通过将基础数据类型更改为修复了上一冲突<xref:System.Int32>。

### <a name="code"></a>代码
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>相关的规则
 [CA1008:枚举应具有零值](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027:用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700:未命名的枚举值 Reserved](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712:不要使用类型名称的枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>请参阅

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>