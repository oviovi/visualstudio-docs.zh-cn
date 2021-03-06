---
title: 将属性添加到项目项 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03faec8cdb79dcaf8bc074328da84af77d1cb17c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766869"
---
# <a name="adding-an-attribute-to-a-project-item"></a>将属性添加到项目项
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>获取和设置的项目项的属性的值。 SetItemAttribute 创建属性，如果已存在，将其添加到项目项元数据。  
  
## <a name="adding-an-attribute-to-a-project-item"></a>将属性添加到项目项  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>将属性添加到项目项  
  
-   下面的代码使用<xref:EnvDTE.DTE>自动化对象和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>方法将属性添加到项目项。 从项目项名称"program.cs"获取项目项 ID。 添加到此项目项属性"即"并将其赋了值"MyValue"。  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>请参阅  
 [保留 MSBuild 项目文件中的数据](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

