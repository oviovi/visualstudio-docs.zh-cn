---
title: CommandPlacement 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5d694f6ed12d3fd7d531ec6a0a01ec70a826561
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941346"
---
# <a name="commandplacement-element"></a>CommandPlacement 元素
CommandPlacement 元素使按钮、 组和要包含在多个组或菜单中的菜单。 通过使用 CommandPlacement 元素，无需完全重新定义这些项，若要修改用户界面的外观。  
  
 有关详细信息，请参阅[创建可重用的按钮组](../extensibility/creating-reusable-groups-of-buttons.md)。  
  
## <a name="syntax"></a>语法  
  
```  
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。 命令集，如中所定义的 guid [Symbols 元素](../extensibility/symbols-element.md)。|  
|id|必需。 菜单、 组或命令放置，如中所定义的 id `Symbols Element`。|  
|priority|必需。 确定项在其父元素中的 visual 位置。|  
|条件|可选。 请参阅[条件 Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|父级|必需。 菜单或托管要放置的项组中。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|指定 CommandPlacements 和 CommandPlacement 元素组。|  
  
## <a name="example"></a>示例  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>请参阅  
 [CommandPlacements 元素](../extensibility/commandplacements-element.md)   
 [Visual Studio 命令表格 (.vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
