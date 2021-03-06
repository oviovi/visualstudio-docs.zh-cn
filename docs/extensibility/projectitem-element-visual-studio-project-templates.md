---
title: ProjectItem 元素 （Visual Studio 项目模板） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2290b8a95bbb2e53ae14f410f77109394528b138
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927358"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 元素 （Visual Studio 项目模板）
指定项目模板中包含的文件。  
  
> [!NOTE]
>  `ProjectItem`元素接受不同的属性，具体取决于该模板是针对某个项目或项。 本主题介绍了`ProjectItem`项目模板的元素。 有关的说明`ProjectItem`元素的项模板，请参阅[ProjectItem 元素 （Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<ProjectItem >  
  
## <a name="syntax"></a>语法  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各部分描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
| 特性 | 描述 |
|---------------------| - |
| `TargetFileName` | 可选特性。<br /><br /> 从模板创建项目时指定的名称和项目项的路径。 此属性可用于在模板中创建的目录结构的目录结构不同 *.zip*文件，或使用参数替换创建的项名称。 |
| `ReplaceParameters` | 可选特性。<br /><br /> 一个布尔值，该值指定项是否可以从模板创建项目时，必须将其替换的参数值。 默认值是 `false`。 |
| `OpenInEditor` | 可选特性。<br /><br /> 一个布尔值，指定此项是否应在其各自编辑器中打开[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]从模板创建项目时。<br /><br /> `OpenInWebBrowser`并`OpenInHelpBrowser`将忽略具有的项上的属性`OpenInEditor`的值`true`。<br /><br /> 默认值为 `false`。 |
| `OpenInWebBrowser` | 可选特性。<br /><br /> 一个布尔值，该值指定项是否应该打开 Web 浏览器从模板创建项目。<br /><br /> 只有 HTML 文件和文本文件是本地的项目可以在 Web 浏览器中打开。 外部 Url 不能打开与此特性。<br /><br /> 默认值为 `false`。 |
| `OpenInHelpBrowser` | 可选特性。<br /><br /> 一个布尔值，该值指定从模板创建项目项是否应在帮助查看器中打开。<br /><br /> 只有 HTML 文件和文本文件是本地的项目可以帮助浏览器中打开。 外部 Url 不能打开与此特性。<br /><br /> 默认值为 `false`。 |
| `OpenOrder` | 可选特性。<br /><br /> 指定数字值，该值表示项将在其各自的编辑器中打开的顺序。 所有值都必须为 10 的倍数。 更高版本的项与`OpenOrder`值首先打开。 |
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|指定的文件或目录将添加到项目。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 一个`string`表示到模板中的文件的名称或路径 *.zip*文件。  
  
## <a name="remarks"></a>备注  
 `ProjectItem` 是的一个可选子级`Project`。  
  
 `TargetFileName`属性可用于在模板中创建的目录结构不同的目录结构 *.zip*文件。 例如，如果该文件*MyFile.vb*存在于模板的根 *.zip*文件，但您想要放在目录中名为的文件*CustomFiles*中的所有项目从模板创建的此时可以使用以下 XML:  
  
```xml  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`属性还可用于重命名文件，其中包含在其文件名中的国际字符。 例如，模板 *.zip*文件不能包含文件名称包含 Unicode 字符，因此必须重命名该文件，然后将其压缩成 *.zip*文件。 `TargetFileName`属性可用于将文件名称设置回原始的 Unicode 文件名。  
  
 `TargetFileName`属性还可用于使用参数重命名文件。 以下过程说明如何将文件重命名*MyFile.vb*，该模板的根目录中存在于其 *.zip*文件、 基于项目名称的文件名称。  
  
### <a name="to-rename-files-with-parameters"></a>若要使用的参数重命名文件  
  
1. 使用在下面的 XML *.vstemplate*文件：  
  
   ```xml  
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
   ```  
  
2. 打开项目文件 (*.vbproj*有关[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]项目) 中的文本编辑器或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
3. 看起来类似于下面的 XML 项目文件中找到的行：  
  
   ```xml  
   <Compile Include="MyFile.vb">  
   ```  
  
4. 代码行替换为以下 XML:  
  
   ```xml  
   <Compile Include="$safeprojectname$.vb">  
   ```  
  
    通过此模板创建项目，文件名称基于用户输入中的名称**新的项目**对话框中的，所有不安全字符和删除空格。 有关详细信息，请参阅[模板参数](../ide/template-parameters.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示用于的项目模板的元数据[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]应用程序。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [模板参数](../ide/template-parameters.md)   
 [ProjectItem 元素（Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)