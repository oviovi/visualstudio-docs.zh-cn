---
title: 工作流设计器-AddToCollection<T>活动设计器
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd8e92baa4192d0b40acdc1d51d01ea339b528c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926745"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > 活动设计器

**AddToCollection\<T >** 活动设计器用于创建和配置<xref:System.Activities.Statements.AddToCollection%601>活动。

## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > 活动

<xref:System.Activities.Statements.AddToCollection%601> 活动向集合添加一项。

### <a name="using-the-addtocollectiont-activity-designer"></a>使用 AddToCollection\<T > 活动设计器

**AddToCollection\<T >** 活动设计器可在**集合**类别**工具箱**，这通过单击访问**工具箱**工作流设计器选项卡。 或者，选择**工具箱**从**视图**菜单中或按**Ctrl**+**Alt** + **X**。

**AddToCollection\<T >** 活动设计器可以从拖动**工具箱**和任何放置活动的如与内部位置放置到工作流设计器图面<xref:System.Activities.Statements.Sequence>. 删除**AddToCollection\<T >** 活动设计器创建<xref:System.Activities.Statements.AddToCollection%601>默认值的活动<xref:System.Activities.Activity.DisplayName%2A>的 AddToCollection < Int32\>。 (默认情况下*TypeArgument*是**Int32**。 TypeArgument 可更改在属性网格中。）<xref:System.Activities.Activity.DisplayName%2A>值可以在的标头中编辑**AddToCollection < T\>** 活动设计器中或在**DisplayName**属性网格的框。 其他属性必须在属性网格上编辑。

### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > 属性

下表列出 <xref:System.Activities.Statements.AddToCollection%601> 属性并说明如何在设计器中使用它们。

|属性名|必需|用法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 活动的友好名称。 默认值为 AddToCollection < Int32\>。 虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|要添加到集合的项\<T >。 此项的类型是*T*，它属于类型*TypeArgument*。 若要指定项，请在属性网格中键入 Visual Basic 表达式。|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|项应添加到的集合。 此集合属于类型**ICollection < TypeArgument\>**。 若要指定集合，请在属性网格中键入 Visual Basic 表达式。|
|*TypeArgument*|True|包含在 <xref:System.Collections.Generic.ICollection%601> 中的项的类型 T。 默认情况下，这*TypeArgument*类型设置为**Int32**。 若要更改的类型，更改的值*TypeArgument*在属性网格中的组合框中。|

## <a name="see-also"></a>请参阅

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > 活动设计器](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)