---
title: 通过使用命令打开显示文件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5ba2aa9ad9a80a820a1ab8311280c3bf2dedc476
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820246"
---
# <a name="display-files-by-using-the-open-with-command"></a>使用打开方式命令显示文件
一个项目可以询问要显示在 IDE**打开**对话框。 此请求会提示用户打开具有的标准编辑器选择的文件。 以下步骤介绍了此过程：  
  
1.  项目调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，将值指定为`OSE_UseOpenWithDialog`为`OSEOpenDocEditor`参数。  
  
2.  基于文档的文件扩展名，IDE 确定列出注册表中的编辑器打开指定的文档，并显示此信息**打开**对话框。  
  
    > [!NOTE]
    >  让中必须包含一个内部函数编辑器的项目**打开**对话框必须用于每个此类编辑器注册编辑器工厂。 内部函数编辑器仅函数以及特定类型的项目，它的实现中强制实施<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。 IDE 提供核心文本编辑器和二进制编辑器内置编辑器工厂。 IDE 还创建编辑器工厂的实例代表每个已注册的 Windows 文件关联。 此类文件的一个示例是 Microsoft Word。  
  
3.  只要用户选择某个项从**打开**对话框中，然后在 IDE 打开文档通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。 有关更多信息，请参见[如何：打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)。  
  
## <a name="see-also"></a>请参阅  
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)   
 [使用打开文件命令显示文件](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [如何：打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)
