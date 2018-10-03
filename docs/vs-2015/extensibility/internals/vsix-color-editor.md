---
title: VSIX 颜色编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3368f61b44dc258651dc20f5de249972074c512
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47478278"
---
# <a name="vsix-color-editor"></a>VSIX 颜色编辑器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[VSIX 颜色编辑器](https://docs.microsoft.com/visualstudio/extensibility/internals/vsix-color-editor)。  
  
Visual Studio 扩展颜色编辑器工具可以创建和编辑 Visual Studio 的自定义颜色。 该工具还可以生成主题的资源键，以便可以在代码中使用的颜色。 此工具可用于使支持主题的 Visual Studio 扩展插件的颜色。 此工具可以打开.pkgdef 和.xml 文件。 通过更改文件扩展名为.xml，visual Studio 主题 （.vstheme 文件） 可以使用与 Visual Studio 扩展颜色编辑器。 此外，可以将.vstheme 文件导入当前的.xml 文件。  
  
 ![VSIX 颜色编辑器 Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX 颜色编辑器 Hero")  
  
 **包定义文件**  
  
 包定义 (.pkgdef) 文件是定义主题的文件。 颜色本身存储在主题颜色.xml 文件，可编译成.pkgdef 文件。 .Pkgdef 文件部署到 Visual Studio 可搜索的位置，在运行时，处理和合并，以定义主题。  
  
 **颜色标记**  
  
 颜色标记由四个元素组成：  
  
-   **类别名称：** 的颜色集的逻辑分组。 如果已有特定于所需的 UI 元素或组的用户界面元素的颜色，请使用现有的类别名称。  
  
-   **令牌名称：** 的颜色标记和标记集的描述性名称。 设置包括背景和前景 （文本） 的标记名称，以及所有其状态，以及这些，因此很容易识别对，并且它们应用于的状态应命名为。  
  
-   **颜色值 （或色调）：** 所需的每个彩色的主题。 始终创建背景和文本颜色值对。 以便始终在其绘制的背景色对可读的文本 （前景） 颜色背景/前景的配对颜色。 这些颜色链接，将在 UI 中一起使用。 如果在后台不专用于与文本一起使用，不要定义前景色。  
  
-   **系统颜色名称：** 在高对比度显示中使用。  
  
## <a name="how-to-use-the-tool"></a>如何使用该工具  
 尽可能多地，并在适当的情况而不是使新的应重复使用现有的 Visual Studio 颜色。 但是，在其中定义没有适当的颜色的情况下，自定义颜色应为创建以保留扩展主题设置兼容。  
  
 **创建新的颜色标记**  
  
 若要创建使用 Visual Studio 扩展颜色编辑器的自定义颜色，请执行以下步骤：  
  
1.  确定新的颜色标记的类别和标记名称。  
  
2.  选择高对比度的 UI 元素将用于每个主题和系统颜色的色调。  
  
3.  使用颜色编辑器创建新的颜色标记。  
  
4.  在 Visual Studio 扩展中使用的颜色。  
  
5.  在 Visual Studio 中测试所做的更改。  
  
 **步骤 1： 确定类别和新的颜色标记的标记名称。**  
  
 首选命名方案为 VSColor **[类别] [UI 类型] [State]**。 不要 VSColor 名称中使用单词"color"，因为它是冗余。  
  
 类别名称提供逻辑分组，而应定义为窄越好。 例如，单个工具窗口的名称可能是一个类别名称，但不是整个业务单元或项目组的名称。 分组为类别的项可帮助防止产生混乱之间具有相同名称的颜色。  
  
 元素类型的情况下或"状态，"颜色将为其应用，必须清楚地指示令牌名称。 例如，活动的数据提示 **[UI 类型]** 可命名为"**数据提示**"和 **[State]** 可命名为"**Active**，"生成中颜色名称"**DataTipActive**。" 由于数据提示文本，前景色和背景色会需要定义。 通过使用背景/前景配对，颜色编辑器将自动创建颜色"**DataTipActive**"背景和"**DataTipActiveText**"的前景。  
  
 如果用户界面具有只有一个状态 **[State]** 名称的一部分，则可以省略。 例如，如果搜索框中有一个边框，并且没有任何状态更改时，会影响边框的颜色，然后边框的颜色标记的名称可以只需调用"**SearchBoxBorder**。"  
  
 一些常见的状态名称包括：  
  
-   活动的  
  
-   非活动状态  
  
-   MouseOver  
  
-   鼠标按下  
  
-   已选定  
  
-   已设定焦点  
  
 列表项控件的部件的几个标记名称的示例：  
  
-   ListItem  
  
-   ListItemBorder  
  
-   ListItemMouseOver  
  
-   ListItemMouseOverBorder  
  
-   ListItemSelected  
  
-   ListItemSelectedBorder  
  
-   ListItemDisabled  
  
-   ListItemDisabledBorder  
  
 **步骤 2： 选择高对比度的 UI 元素将用于每个主题和系统颜色的色调。**  
  
 在自定义颜色选择 ui 时，选择类似现有的 UI 元素，并为基础使用它的颜色。 框中的 UI 元素的颜色经过了检查和测试，因此它们将查找适当并在所有主题中的正确行为。  
  
 **步骤 3： 使用颜色编辑器创建新的颜色标记。**  
  
 启动颜色编辑器和打开或创建新的自定义主题颜色.xml 文件。 选择**编辑 > 新颜色**菜单中。 这将打开一个对话框用于指定类别，该类别中颜色条目的一个或多个名称：  
  
 ![VSIX 颜色编辑器新颜色](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX 颜色编辑器新颜色")  
  
 选择现有类别，或选择**新类别**若要创建新类别。 将打开另一个对话框，创建一个新的类别名称：  
  
 ![VSIX 颜色编辑器新类别](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX 颜色编辑器新类别")  
  
 然后会在中可用的新类别**新颜色**类别下拉列表菜单。 在选择一个类别之后, 输入每个新的颜色标记每行一个名称并选择"创建"完成后：  
  
 ![VSIX 颜色编辑器新颜色填充](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX 颜色编辑器新颜色填充")  
  
 颜色值背景/前景对中所示的"无"，该值指示尚未定义颜色。 注意： 如果颜色不具有文本颜色/背景颜色对，然后仅在后台需要定义。  
  
 ![VSIX 颜色编辑器颜色值](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX 颜色编辑器颜色值")  
  
 若要编辑颜色标记，请选择该令牌的主题 （列） 的颜色条目。 通过采用 8 位 ARGB 格式键入十六进制颜色值，在单元格中，进入系统的颜色名称或使用下拉列表菜单来选择所需的颜色通过一组颜色滑块或系统颜色的列表中添加的颜色值。  
  
 ![VSIX 颜色编辑器编辑颜色](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX 颜色编辑器编辑颜色")  
  
 ![VSIX 颜色编辑器背景](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX 颜色编辑器背景")  
  
 对于不需要显示文本的组件，请输入一个颜色值： 背景色。 否则，输入的文本和背景色，由正斜杠分隔的值。  
  
 高对比度的输入值时, 输入有效的 Windows 系统颜色名称。 不要输入 ARGB 硬编码值。 可以通过从颜色值下拉列表菜单中选择"背景:: 系统"或"前景色:: 系统"来查看有效的系统颜色名称的列表。 创建具有文本组件的元素时，使用正确的背景文本系统颜色对或文本可能是不可读。  
  
 完成创建、 设置和编辑的颜色标记的操作之后，将它们保存到所需的.xml 或.pkgdef 格式。 令牌具有两背景的颜色也前台集将保存为.xml 格式的空颜色，但.pkgdef 格式中将被丢弃。 如果你尝试将空颜色保存到.pkgdef 文件，对话框会警告您可能颜色丢失。  
  
 **步骤 4： 使用 Visual Studio 扩展中的颜色。**  
  
 定义新的颜色后令牌，使用"生成操作"设置为"Content"在项目文件中包含.pkgdef 和"包括在 VSIX"设置为"True。  
  
 ![VSIX 颜色编辑器 pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX 颜色编辑器 pkgdef")  
  
 在 Visual Studio 扩展颜色编辑器中，选择文件 > 基于 WPF 的 UI 中查看资源代码查看代码，用于访问自定义颜色。  
  
 ![VSIX 颜色编辑器资源代码查看器](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX 颜色编辑器资源代码查看器")  
  
 在项目中的静态类中包括此代码。 对引用**Microsoft.VisualStudio.Shell。\<VSVersion >.0.dll**需要添加到项目以使用**ThemeResourceKey**类型。  
  
```csharp  
namespace MyCustomColors  
{  
    public static class MyCategory  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");  
  
        private static ThemeResourceKey _MyColor1ColorKey;  
        private static ThemeResourceKey _MyColor1BrushKey;  
        private static ThemeResourceKey _MyColor1TextColorKey;  
        private static ThemeResourceKey _MyColor1TextBrushKey;  
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }  
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }  
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }  
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }  
        #endregion  
    }  
}  
```  
  
 这可以访问 XAML 代码中的颜色，并允许 UI 的主题更改进行响应。  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"  
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
             xmlns:ns="clr-namespace:MyCustomColors">  
  <Grid>  
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"  
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"  
      >Sample Text</TextBlock>  
  
  </Grid>  
</UserControl>  
```  
  
 **步骤 5： 在 Visual Studio 中测试所做的更改。**  
  
 颜色编辑器可以暂时将颜色标记应用于 Visual Studio 以查看实时更改颜色，而无需重新生成扩展包的运行实例。 若要执行此操作，请单击位于每个主题列标题上的"将此主题应用于运行 windows 的 Visual Studio"按钮。 VSIX 颜色编辑器关闭时，此临时主题将消失。  
  
 ![VSIX 颜色编辑器应用](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX 颜色编辑器应用")  
  
 若要永久所做的更改，重新生成并向.pkgdef 文件添加新的颜色和编写代码，将使用这些颜色后重新部署 Visual Studio 扩展。 重新生成的 Visual Studio 扩展将合并到主题的其余部分中的新颜色的注册表值。 然后重新启动 Visual Studio 中，查看 UI，并验证新颜色按预期方式显示。  
  
## <a name="notes"></a>说明  
 此工具旨在用于创建自定义颜色为预先存在的 Visual Studio 主题，或编辑自定义 Visual Studio 主题的颜色。 若要创建完整的自定义 Visual Studio 主题，请下载[Visual Studio 颜色主题编辑器扩展](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b)从 Visual Studio 扩展库。  
  
## <a name="sample-output"></a>示例输出  
 **XML 颜色输出**  
  
 由工具生成的.xml 文件将类似于此：  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">  
      <Color Name="ColorName1">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
      <Color Name="ColorName2">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
        <Foreground Type="CT_RAW" Source="FF000000" />  
      </Color>  
      <Color Name="ColorName3">  
        <Background Type="CT_RAW" Source="FFFF0000" />  
      </Color>  
      <Color Name="ColorName4">  
        <Background Type="CT_RAW" Source="FF000088" />  
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
    </Category>  
  </Theme>  
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>  
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>  
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>  
</Themes>  
  
```  
  
 **PKGDEF 颜色输出**  
  
 由工具生成.pkgdef 文件将类似于此：  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]  
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff  
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]  
"Data"=hex:...  
  
```  
  
 **C# 资源密钥包装器**  
  
 由工具生成的颜色资源密钥将类似于此：  
  
```csharp  
namespace MyNamespace  
{  
    public static class MyColors  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
  
        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }  
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }  
  
        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }  
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }  
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }  
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }  
  
        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }  
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }  
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }  
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }  
        #endregion  
    }  
}  
```  
  
 **WPF 资源字典包装器**  
  
 颜色**ResourceDictionary**由工具生成的密钥将类似于此：  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:colors="clr-namespace:MyNamespace">  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />  
</ResourceDictionary>  
```
