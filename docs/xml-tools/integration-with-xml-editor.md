---
title: XML 架构设计器集成与 XML 编辑器
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a4d97ce590929b6cc2cf56997255822b692cc9e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865006"
---
# <a name="integration-with-xml-editor"></a>与 XML 编辑器集成

XML 编辑器中集成了 XML 架构设计器。 如果您修改 XSD 文件在 XML 编辑器中，更改将反映在[XML 架构资源管理器](../xml-tools/xml-schema-explorer.md)。 如果有[关系图视图](../xml-tools/graph-view.md)或[内容模型视图](../xml-tools/content-model-view.md)打开，更改也会反映在存在。 可通过以下方法在 XML 架构设计器和 XML 编辑器之间导航：

-   在 XML 编辑器中，右键单击某个节点并选择**在 XML 架构资源管理器中显示**。

-   关系图视图中， **XML 架构资源管理器**，双击某个节点，或右键单击某个节点并选择**查看代码**。 在内容模型视图中，右键单击某个节点并选择**查看代码**。

下面的屏幕截图显示在中打开一个 XML 架构**XML 架构资源管理器**。 **XML 架构资源管理器**显示在树视图中设置的架构。 XML 编辑器显示当前处于活动状态中的节点的文本视图**XML 架构资源管理器**。

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

有时，在 XML 编辑器中和在图形设计器中并行查看代码是很有帮助的。 若要同时查看这两个文件，请右键单击任意位置在 XML 编辑器中，并选择**视图设计器**。 在 Visual Studio Windows 菜单中，选择**新水平 （或垂直） 选项卡组**。

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>请参阅

- [XML 架构资源管理器](../xml-tools/xml-schema-explorer.md)