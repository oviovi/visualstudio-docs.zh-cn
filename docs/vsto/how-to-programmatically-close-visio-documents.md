---
title: 如何：以编程方式关闭 Visio 文档
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 499cc399c1e23c6f045426e57f8e9a027b5c6537
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091788"
---
# <a name="how-to-programmatically-close-visio-documents"></a>如何：以编程方式关闭 Visio 文档
  可以使用 `Microsoft.Office.Interop.Visio.Document.Close` 方法关闭活动 Microsoft Office Visio 文档。  
  
 有关此方法的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) 方法的 VBA 参考文档。  
  
## <a name="close-the-active-document"></a>关闭活动文档  
  
### <a name="to-close-the-active-document"></a>关闭活动文档  
  
-   调用 `Microsoft.Office.Interop.Visio.Document.Close` 方法关闭活动文档。  
  
     若要使用下面的代码示例，请运行`ThisAddIn`Visio 的 VSTO 外接程序项目中的类。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [如何：以编程方式创建新的 Visio 文档](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以编程方式打开 Visio 文档](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何：以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)  
