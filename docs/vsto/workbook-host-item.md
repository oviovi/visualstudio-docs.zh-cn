---
title: 工作簿主机项
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f15d93818c2db553d22d9639e6460f6637d33c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952852"
---
# <a name="workbook-host-item"></a>工作簿主机项
  <xref:Microsoft.Office.Tools.Excel.Workbook> 宿主项这种类型从 Excel 的主互操作程序集扩展 <xref:Microsoft.Office.Interop.Excel.Workbook> 类型。 <xref:Microsoft.Office.Tools.Excel.Workbook> 宿主项提供与 <xref:Microsoft.Office.Interop.Excel.Workbook> 对象完全相同的属性、方法和事件，但它还提供其他功能。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 在文档级项目中，有一个表示项目中的工作簿的默认 <xref:Microsoft.Office.Tools.Excel.Workbook> 宿主项。 在 VSTO 外接程序项目中，您可以生成<xref:Microsoft.Office.Tools.Excel.Workbook>主机在运行时的项。  
  
## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>了解文档级项目中的工作簿主机项  
 若要访问项目中的工作簿，请使用 `ThisWorkbook` 类。 通过使用 `ThisWorkbook` 类，可以访问 <xref:Microsoft.Office.Tools.Excel.Workbook> 宿主项的成员，以执行自定义项中的基本任务，例如在打开或关闭工作簿时运行代码。 有关详细信息，请参阅[程序文档级自定义项](../vsto/programming-document-level-customizations.md)。  
  
 `ThisWorkbook` 类提供了一个位置，你可以在该位置开始编写项目中的代码。 因为该类提供与 Excel 主互操作程序集中的 <xref:Microsoft.Office.Interop.Excel.Workbook> 对象完全相同的属性、方法和事件，所以也可以使用 `ThisWorkbook` 访问 Excel 的对象模型。 有关详细信息，请参阅[Excel 对象模型概述](../vsto/excel-object-model-overview.md)。  
  
 在“解决方案资源管理器”  中双击“ThisWorkbook”  项目项以显示工作簿设计器，并在“属性”  窗口中查看工作簿的属性和事件。  
  
### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>文档级项目中的工作簿主机项的限制  
 文档级项目只能包含一个 <xref:Microsoft.Office.Tools.Excel.Workbook> 宿主项（即 `ThisWorkbook` 类）。 您不能添加新<xref:Microsoft.Office.Tools.Excel.Workbook>主机在设计时，对你的项目项并不能创建新条目<xref:Microsoft.Office.Tools.Excel.Workbook>主机在运行时从文档级自定义项。  
  
 如果在运行时创建新的 Excel 工作簿，它将是类型<xref:Microsoft.Office.Interop.Excel.Workbook>。 因为它不是宿主项，所以它不能包含任何宿主控件或 Windows 窗体控件。 有关在运行时创建工作簿的详细信息，请参阅[如何：以编程方式创建新的工作簿](../vsto/how-to-programmatically-create-new-workbooks.md)。  
  
 <xref:Microsoft.Office.Tools.Excel.Workbook> 宿主项不充当宿主控件的容器。 因此，不能将任何可见控件添加到工作簿，但可以添加 <xref:System.Data.DataSet>等组件，以便这些组件可由所有工作表共享。 在文档级项目中，可用于工作簿的组件可在“工具箱”  的“组件”  选项卡、“数据”  选项卡和“所有 Windows 窗体” 选项卡中找到。  
  
> [!NOTE]  
>  Visual Studio 中的 Office 开发工具不支持共享工作簿。  
  
## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>了解 VSTO 外接程序项目中的工作簿宿主项  
 在 VSTO 外接程序项目中，您可以生成<xref:Microsoft.Office.Tools.Excel.Workbook>在运行时为在 Excel 中打开任何工作簿主机项。 若要生成 <xref:Microsoft.Office.Tools.Excel.Workbook> 主机项，请使用 `GetVstoObject` 方法。 有关详细信息，请参阅[扩展 Word 文档和 Excel 工作簿中运行时在 VSTO 加载项](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## <a name="see-also"></a>请参阅  
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [扩展 Word 文档和 Excel 工作簿在 VSTO 外接在运行时](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [工作表主机项](../vsto/worksheet-host-item.md)   
 [通过使用扩展的对象自动化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主机项和主机控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
