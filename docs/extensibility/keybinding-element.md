---
title: KeyBinding 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c401b1f5179fa03dbd43ffbcff3bd2f0151340c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931666"
---
# <a name="keybinding-element"></a>KeyBinding 元素
键绑定元素指定的命令的键盘快捷方式。  
  
 命令可以具有与之关联的单个和双键绑定。 单个键绑定的一个示例是**Ctrl**+**S**有关**保存**命令。 双键绑定需要两个连续的键组合来触发命令。 双键绑定的一个示例是<strong>Ctrl*+</strong>K<strong>，</strong>Ctrl<strong>+</strong>K** 若要设置书签。  
  
## <a name="syntax"></a>语法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。|  
|id|必需。|  
|编辑器|必需。 编辑器 GUID 指示为其此键盘快捷方式将处于活动状态的编辑上下文。 全局绑定作用域值为"guidVSStd97"。|  
|key1|必需。 有效值包括所有键入是字母数字，以及两位数字的十六进制值以 0x 开头并[VK_constants](/windows/desktop/inputdev/virtual-key-codes)。|  
|mod1|可选。 任意组合**Ctrl**， **Alt**，并**Shift**通过空格分隔开来。|  
|key2|可选。 有效值包括所有键入是字母数字，以及两位数字的十六进制值以 0x 开头并[VK_constants](/windows/desktop/inputdev/virtual-key-codes)。|  
|mod2|可选。 任意组合**Ctrl**， **Alt**，并**Shift**通过空格分隔开来。|  
|仿真程序|可选。|  
|条件|可选。 请参阅[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|父级||  
|批注||  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[KeyBindings 元素](../extensibility/keybindings-element.md)|键绑定元素进行分组和其他键绑定分组。|  
  
## <a name="example"></a>示例  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>请参阅  
 [KeyBindings 元素](../extensibility/keybindings-element.md)   
 [Visual Studio 命令表格 (.vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
