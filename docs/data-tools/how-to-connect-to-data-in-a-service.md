---
title: 如何：连接到服务中的数据
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f8f7371418df19ec8452334641c7c9414328e557
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305008"
---
# <a name="how-to-connect-to-data-in-a-service"></a>如何：连接到服务中的数据

通过运行从服务返回的数据将应用程序连接[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)，然后选择**服务**上**选择数据源类型**页。

在向导完成，服务引用添加到你的项目，并可立即在[数据源窗口](add-new-data-sources.md#data-sources-window)。

> [!NOTE]
> “数据源”**窗口中显示的项取决于该服务返回的信息。 某些服务可能没有为“数据源配置向导”**创建可绑定的对象提供足够的信息。 例如，如果该服务返回的非类型化数据集，显示任何项中**数据源**完成该向导时的窗口。 这是因为非类型化数据集不提供架构，所以该向导没有足够的信息来创建数据源。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>若要连接到服务应用程序

1.  在 **“数据”** 菜单上，单击 **“添加新数据源”**。

2.  选择**服务**上**选择数据源类型**页上，然后依次**下一步**。

3.  输入你想要使用，或单击该服务的地址**Discover**若要在当前解决方案中，找到服务，然后单击**转**。

4.  （可选） 您可以键入一个新**Namespace**默认值的位置。

    > [!NOTE]
    > 单击**高级**以打开[配置服务引用对话框](../data-tools/configure-service-reference-dialog-box.md)。

5.  单击**确定**添加到你的项目的服务引用。

6.  单击 **“完成”**。

     ** 数据源随即添加到{2&gt;“数据源”&lt;2}窗口中。

## <a name="next-steps"></a>后续步骤

若要将功能添加到你的应用程序中，选择中的项**数据源**窗口并将其拖到窗体来创建绑定的控件。 有关详细信息，请参阅[将控件绑定到 Visual Studio 中的数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="see-also"></a>请参阅

- [将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio 中的 Windows Communication Foundation 服务和 WCF 数据服务](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)