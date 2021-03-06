---
title: 工作流设计器-如果活动设计器
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de237acd09f4c4139bdf79f986dbb43c1a1f8343
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988412"
---
# <a name="if-activity-designer"></a>If 活动设计器

<xref:System.Activities.Statements.If> 活动计算条件并根据该计算结果执行活动。 当使用编程的过程建模样式时，此活动最有用。 例如，<xref:System.Activities.Statements.If> 活动可嵌套在 <xref:System.Activities.Statements.Sequence> 活动或 <xref:System.Activities.Statements.Parallel> 活动内。 如果您使用的是 <xref:System.Activities.Statements.Flowchart> 活动，请考虑改用 <xref:System.Activities.Statements.FlowDecision> 活动。

## <a name="if-properties-in-the-workflow-designer"></a>工作流设计器中的 If 属性

下表列出最有用的 <xref:System.Activities.Statements.If> 活动属性并说明如何在设计器中使用它们。

|属性名|必需|用法|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|用于确定要执行哪个子活动的条件。 若要设置<xref:System.Activities.Statements.If.Condition%2A>，键入 Visual Basic 表达式**条件**框**如果**活动设计器或在属性网格中。|
|<xref:System.Activities.Statements.If.Else%2A>|False|要执行的活动<xref:System.Activities.Statements.If.Condition%2A>是**false**。 若要添加活动，则由<xref:System.Activities.Statements.If.Else%2A>分支中，将活动从**工具箱**到**Else**框**如果**带提示文本的活动设计器"在此处放置活动"。|
|<xref:System.Activities.Statements.If.Then%2A>|False|要执行的活动<xref:System.Activities.Statements.If.Condition%2A>是**true**。 若要添加活动，则由<xref:System.Activities.Statements.If.Then%2A>分支中，将活动从**工具箱**到**然后**框**如果**带提示文本的活动设计器"在此处放置活动"。|

## <a name="see-also"></a>请参阅

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [控制流](../workflow-designer/control-flow-activity-designers.md)