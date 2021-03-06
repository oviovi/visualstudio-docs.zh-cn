---
title: 提供撤消向设计器支持 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eef024c14dfcab515d0205f7e1298020dbd3bd91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836291"
---
# <a name="supplying-undo-support-to-designers"></a>向设计器提供撤消支持
设计器中的，等编辑器，通常需要支持撤消操作，以便修改代码元素时，用户可以撤消他们最近的更改。  
  
 在 Visual Studio 中实现的大多数设计器都有撤消支持自动提供的环境。  
  
 需要撤消功能提供支持的设计器实现：  
  
- 通过实现的抽象基类提供撤消管理 <xref:System.ComponentModel.Design.UndoEngine>  
  
- 通过实现来支持提供持久性和 CodeDOM<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>类。  
  
  有关编写使用设计器的详细信息[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，请参阅[扩展设计时支持](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)。  
  
  [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供的默认撤消基础结构：  
  
- 提供撤消管理实现通过<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>和<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>类。  
  
- 提供持久性和 CodeDOM 支持通过默认<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>实现。  
  
## <a name="obtaining-undo-support-automatically"></a>自动获取撤消支持  
 在中创建任何设计器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]具有自动和完全撤消支持 if、 设计器：  
  
-   利用<xref:System.Windows.Forms.Control>基于其用户界面的类。  
  
-   为代码生成和持久性采用标准基于 CodeDOM 的代码生成和分析系统。  
  
     有关如何使用 Visual Studio CodeDOM 支持的详细信息，请参阅[动态源代码生成和编译](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>何时使用显式设计器的撤消支持  
 如果他们使用称为视图适配器，不是由提供的图形用户界面设计器必须提供其自己撤消管理<xref:System.Windows.Forms.Control>。  
  
 出现这种可能会创建一个产品具有基于 web 的图形设计界面而不是一个[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]基于图形界面。  
  
 在这种情况下，则你需要注册使用此视图适配器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>，并提供一个显式撤消管理。  
  
 需要提供 CodeDOM 和持久性支持，如果它们不使用设计器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中提供的代码生成模型<xref:System.CodeDom>命名空间。  
  
## <a name="undo-support-features-of-the-designer"></a>撤消支持功能的设计器  
 环境 SDK 提供的接口提供所需的默认实现撤消支持，可由设计器不使用<xref:System.Windows.Forms.Control>基于其用户界面或标准的 CodeDOM 和持久性模型的类。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>类派生自[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]<xref:System.ComponentModel.Design.UndoEngine>类使用的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>类来管理撤消操作。  
  
 Visual Studio 提供了以下功能，到设计器撤消：  
  
- 跨多个设计器的链接的撤消功能。  
  
- 其父级进行交互的子单元的设计器中可以通过实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>并<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>上<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>。  
  
  环境 SDK 提供 CodeDOM 和持久性支持通过提供：  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 作为的实现 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  一个<xref:System.ComponentModel.Design.IComponentChangeService>提供的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' 设计宿主。  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>使用环境 SDK 功能来提供撤消支持  
 若要获取撤消支持，实现设计器的对象必须：  
  
- 实例化和初始化的实例<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>类的有效<xref:System.IServiceProvider>实现。  
  
- 这<xref:System.IServiceProvider>类必须提供以下服务：  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>。  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
     使用设计器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]CodeDOM 序列化可能选择使用<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>随附[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]作为其实现的<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>。  
  
     在这种情况下，<xref:System.IServiceProvider>类提供给<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>构造函数应返回此对象的实现作为<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>类。  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
     使用默认的设计器<xref:System.ComponentModel.Design.DesignSurface>提供的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]设计宿主可以保证的默认实现<xref:System.ComponentModel.Design.IComponentChangeService>类。  
  
  设计器实现<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>如果基于的撤消机制可自动跟踪更改：  
  
- 通过进行属性更改<xref:System.ComponentModel.TypeDescriptor>对象。  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> 提交可撤消更改时，手动生成事件。  
  
- 在设计器上的进行修改的上下文中创建<xref:System.ComponentModel.Design.DesignerTransaction>。  
  
- 在设计器中选择显式创建撤消单元使用的实现所提供的标准的撤消单元<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>或 Visual Studio 的特定于实现<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>，它派生<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>，还提供了这两者的实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [扩展设计时支持](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)