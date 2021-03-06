---
title: 工作流设计器的 Receive 活动设计器
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86c2d67d3922679096a3b3980a928a234515b78e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858986"
---
# <a name="receive-activity-designer"></a>Receive 活动设计器

**接收**活动设计器用于创建和配置<xref:System.ServiceModel.Activities.Receive>活动。 <xref:System.ServiceModel.Activities.Receive> 活动是接收消息的活动，可接收的消息包括内置类型（如 <xref:System.ServiceModel.Channels.Message>、<xref:System.IO.Stream> 或 <xref:System.Xml.Linq.XElement>）或者应用程序定义的数据协定、消息协定或可序列化的 XML 类。

## <a name="the-receive-activity"></a>Receive 活动

<xref:System.ServiceModel.Activities.Receive> 活动可以接收一个或多个项，具体取决于所用接收内容的类型。 <xref:System.ServiceModel.Activities.SendReply> 活动可绑定到作为服务上请求/响应消息交换模式的一部分接收消息的 <xref:System.ServiceModel.Activities.Receive> 活动。

### <a name="using-the-receive-activity-designer"></a>使用 Receive 活动设计器

访问**接收**中的活动设计器**消息传送**类别**工具箱**。 **接收**活动设计器可以从拖动**工具箱**和任何通常放置活动的位置放置到工作流设计器图面。 这将创建具有 Receive 的默认 <xref:System.ServiceModel.Activities.Receive> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**接收**活动设计器中或在**DisplayName**属性网格的框。

若要创建<xref:System.ServiceModel.Activities.SendReply>活动并将其绑定到所选<xref:System.ServiceModel.Activities.Receive>活动中，右键单击**接收**活动设计器中，单击**创建 SendReply**的上下文菜单中的项和**SendReplyToReceive**如下所示设计器**接收**设计器。 <xref:System.ServiceModel.Activities.SendReply> 活动是作为服务上请求/响应消息交换模式的一部分发送答复消息的一个活动。 可以使用配置**SendReplyToReceive**设计器。

或者， **ReceiveAndSendReply**中的模板设计器**消息传送**类别**工具箱**可用于创建一对预配置<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活动。 有关使用详细信息**ReceiveAndSendReply**并**SendReplyToReceive**模板，请参阅[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)主题。

### <a name="the-receive-activity-properties"></a>Receive 活动属性

下表列出 <xref:System.ServiceModel.Activities.Receive> 属性并说明如何在设计器中使用它们。 在属性网格中或在工作流设计器图面上，可以编辑这些属性。 唯一必需的属性是 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 属性。


| 属性名 | 必需 | 用法 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | 指定 <xref:System.ServiceModel.Activities.Receive> 活动的友好名称。 默认值为 Receive。<br /><br /> 虽然对友好 <xref:System.Activities.Activity.DisplayName%2A> 使用非默认值不是绝对必需的，但最好使用非默认值。 |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | 指定由此 <xref:System.ServiceModel.Activities.Receive> 活动实现的服务操作的名称。 此属性用于构造的默认值为**操作**属性如果**操作**属性未显式设置。 |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | 指定服务协定的名称。 此属性用于将服务操作分组至各个服务协定。 所有具有相同的 <xref:System.ServiceModel.Activities.Receive> 的 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 活动都分组到同一服务协定（WSDL 端口类型）中。 默认值为顶级 （根） 活动的完全限定的 CLR 名称。 |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | 指定要接收的消息或参数内容。 它可为 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活动或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活动。 编辑此属性通过选择旁的省略号按钮**内容**字段在属性网格或单击**定义...** 按钮旁边**内容**上的标签**接收**活动设计器图面。 两者都显示**内容定义**对话框。 有关如何使用此框的详细信息，请参阅[内容定义对话框](../workflow-designer/content-definition-dialog-box.md)主题。 |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | 使用 <xref:System.ServiceModel.Activities.Receive> 对象指定工作流的服务操作中各 <xref:System.ServiceModel.MessageQuerySet> 活动之间的关联。 单击省略号按钮旁边<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>属性在属性网格中，打开**CorrelatesOn 定义**对话框。 有关使用此对话框的详细信息，请参阅[内容定义对话框](../workflow-designer/content-definition-dialog-box.md)主题。 |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | 指定用于将消息路由到相应工作流实例的 <xref:System.ServiceModel.Activities.CorrelationHandle>。<br /><br /> 单击省略号按钮旁边<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A>属性在属性网格中，打开**表达式编辑器**对话框。 有关使用此对话框的详细信息，请参阅[如何：使用表达式编辑器](../workflow-designer/how-to-use-the-expression-editor.md)主题。 |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | 指定在工作流中对配置此 <xref:System.ServiceModel.Activities.CorrelationInitializer> 活动的多个 <xref:System.ServiceModel.Activities.CorrelationHandle> 对象进行初始化的 <xref:System.ServiceModel.Activities.Receive> 对象的集合。 单击省略号按钮旁边<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>属性在属性网格中，打开**添加相关初始值设定项**对话框。 有关使用此框的详细信息，请参阅[添加相关初始值设定项对话框](../workflow-designer/add-correlationinitializers-dialog-box.md)主题。 |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | 指定一个值，该值确定如果消息未关联到现有的工作流实例，是否创建一个新工作流实例来处理该消息。 如果值设置为 **，则返回 true**，创建一个新的工作流实例来处理该消息时消息未关联到现有工作流实例。 |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | 指定由此 <xref:System.ServiceModel.Activities.Receive> 活动实现的服务操作的已知类型集合。 此属性应与设置为 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 的 <xref:System.Runtime.Serialization.DataContractSerializer> 属性结合使用。 如果使用了 <xref:System.Xml.Serialization.XmlSerializer>，则忽略此项。<br /><br /> 选择旁的省略号按钮**KnownTypes**字段中要显示的属性网格**类型集合编辑器**对话框可以添加相关类型。 有关使用此框的详细信息，请参阅[类型集合编辑器对话框](../workflow-designer/type-collection-editor-dialog-box.md)主题。 |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | 指定消息的 <xref:System.Net.Security.ProtectionLevel>。<br /><br /> 1。<xref:System.Net.Security.ProtectionLevel>意味着仅使用身份验证。<br />2。<xref:System.Net.Security.ProtectionLevel>意味着登录数据，以帮助确保传输数据的完整性。<br />3。<xref:System.Net.Security.ProtectionLevel>方法进行加密和签名数据，以帮助确保保密性和传输数据的完整性。 |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | 指定 <xref:System.ServiceModel.Activities.Receive> 活动实现的服务操作所使用的序列化程序的类型。 默认值为 <xref:System.Runtime.Serialization.DataContractSerializer>，它使用提供的数据协定将类型实例序列化和反序列化为 XML 流或文档。 如果需要对 XML 进行更多控制，还可使用 <xref:System.Xml.Serialization.XmlSerializer>。 |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | 指定消息的操作标头。 如果显式设置，其默认值为： https://tempuri.org/{service协定命名空间} / {服务协定名称} / {操作名称}。 |

## <a name="see-also"></a>请参阅

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)