---
title: 建立用户需求模型 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ab92a08aa7359aa4393b3356384a4ccc352afb27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776481"
---
# <a name="model-user-requirements"></a>建立用户需求模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

通过绘制有关用户的活动和你的系统在帮助他们实现自己目标上所起到的作用的关系图，Visual Studio 可帮助你了解你的用户，并与他们展开讨论、沟通其要求。 需求模型是一组这样的关系图，每一张图都将重点放在用户需求的不同方面。 有关视频演示，请参阅： [业务域建模](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)。  
  
 若要查看支持每种类型的模型的 Visual Studio 版本，请参阅 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 需求模型可帮助你：  
  
- 将系统的外部行为与其内部设计区分开来进行重点关注。  
  
- 与使用自然语言相比，在描述用户和利益相关者的需求方面产生的歧义更少。  
  
- 定义可供用户、开发人员和测试人员使用的一致术语术语表。  
  
- 减小要求的差距和不一致性。  
  
- 减少对更改要求作出响应所需的工作量。  
  
- 计划未来开发各种功能的顺序。  
  
- 使用模型作为系统测试的基础，明确测试和要求之间的关系。 要求发生改变时，这种关系将帮助你正确地更新测试。 这可以确保系统满足新的要求。  
  
  如果在与用户或其代表进行重点讨论时使用需求模型，并在每次迭代开始时重新查看需求模型，那么使用需求模型会获得最大的好处。 无需在编写代码之前详细地完成它。 即使是非常简单的部分工作的应用程序，通常也能构成与用户讨论需求时的最具激励性的基础。 模型是汇总讨论结果的一种有效方式。 有关详细信息，请参阅[在您的开发过程中使用模型](../modeling/use-models-in-your-development-process.md)。  
  
> [!NOTE]
>  在这些主题中，“系统”表示正在开发的系统或应用程序。 它可能是许多软件和硬件组件的大型集合、单个应用程序或一个更大型系统内的某个软件组件。 在每种情况下，需求模型都描述了在系统外部可以通过用户界面或 API 看到的行为。  
  
## <a name="common-tasks"></a>常规任务  
 可以根据用户需求创建多个不同的视图。  每个视图都提供特定类型的信息。  在创建这些视图时，最好经常在视图间移动。 可以从任意视图开始。  
  
|关系图或文档|需求模型中描述的内容|节|  
|-------------------------|-----------------------------------------------|-------------|  
|用例图|系统的使用者是谁以及用该系统进行了什么操作。|[描述如何使用您的系统](#UseCases)|  
|概念类图|用于描述要求的类型术语表；类型可以在系统界面中看到。|[定义用于描述要求的术语](#RequirementsClasses)|  
|活动图|由用户与系统或其部件执行的活动之间的工作流和信息。|[显示用户与系统之间的工作流](#Workflow)|  
|序列图|用户和系统或其部分之间的交互序列。 活动图的替代视图。|[显示用户与系统之间的交互](#Sequences)|  
|附加文档或工作项|性能、安全性、可用性和可靠性条件。|[描述服务质量要求](#QoSRequirements)|  
|附加文档或工作项|不针对特定用例的约束和规则|[显示业务规则](#BusinessRules)|  
  
 请注意，大多数关系图类型可以用于其他目的。 有关关系图类型的概述，请参阅[为您的应用程序创建模型](../modeling/create-models-for-your-app.md)。 有关绘制关系图的基本信息，请参阅[编辑 UML 模型和关系图](../modeling/edit-uml-models-and-diagrams.md)。  
  
##  <a name="UseCases"></a> 描述如何使用您的系统  
 创建用例图来描述系统的使用者以及他们使用系统的用途。 用例子表示系统用户的目标，以及他们执行操作以达到目标的过程。  
  
 例如，在线售餐系统必须允许顾客从菜单中选择项目，也必须允许提供服务的餐厅可以更新菜单。 可以在用例图中对此进行汇总：  
  
 ![Customer 和 Restaurant 用例](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")  
  
 也可以展示多个小事例如何构成一个用例。 例如，订餐是购买餐食的一部分，还包括付款和送餐：  
  
 ![系统参与支付，但不是参与交付。](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")  
  
 此外，也可以显示正在开发的系统范围内还包括了哪些用例。 例如，插图中的系统未包含送餐用例。 这有助于为开发工作设置上下文。 （在用例图中，子系统容器可用于表示该系统或其组件。）  
  
 它还可以帮助你的团队讨论后续版本中将包含的内容。 例如，在系统的初始版本中而不是在整个系统，可以讨论餐费支付是否直接安排在餐厅和顾客之间。 在这种情况下，可以在初始版本中将支付餐费移到“立即就餐”系统矩形外。  
  
 用例图仅提供用例的摘要。 若要提供更详细的说明，可以将关系图上的用例链接到单独的文档和其他关系图。 若要了解如何执行此操作，请参阅[用例链接到文档和关系图](../modeling/link-a-use-case-to-documents-and-diagrams.md)。  
  
 绘制用例图可帮助团队：  
  
- 专注于用户期望借助系统执行的操作，而不会被实现的详细信息转移注意力。  
  
- 讨论系统范围或系统的特定版本。  
  
  下列主题提供了更多信息：  
  
|了解|读取|  
|--------------------|----------|  
|有关如何创建用例的更详细信息|[UML 用例图：准则](../modeling/uml-use-case-diagrams-guidelines.md)|  
|用例图上的元素|[UML 用例图：参考](../modeling/uml-use-case-diagrams-reference.md)|  
|如何从用例中开发代码|[应用体系结构建模](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="RequirementsClasses"></a> 定义用于描述要求的术语  
 可以使用 UML 类图来帮助开发一致的、用于以下用途的业务概念术语：  
  
- 由用户自身讨论系统要作用于的业务。  
  
- 描述用户的需求，例如在用例、业务规则和用户情景的描述中。  
  
- 在系统的 API 或通过用户界面交换的信息类型。  
  
- 系统或验收测试的描述。  
  
  当用于此目的时，UML 类图的内容被称为概念类图。 （也称为 *域模型* 或 *分析类模型*。）  
  
  在概念类图中，仅显示要求说明中必须的类，无需显示系统内部设计的任何详细信息。 关系图不会显示系统内部设计的任何详细信息。 通常不会显示概念类上的操作或界面。  
  
  例如，可以为“立即就餐”系统绘制这些概念类：  
  
  ![类菜单、 顺序、 菜单项进行排序项。](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")  
  
  概念类图将提供在整个需求模型中使用的术语词汇。 例如，在用例“订餐”的详细描述中，可能会这样编写：  
  
  顾客选择“菜单”  并从中构造“订单” ，然后通过选择“菜单”  中的“菜单项”  在“订单”  中创建“订单项” 。  
  
  请注意，术语在说明中的使用方法即为模型中类的名称。 关系图可以清楚地说明这些类之间的关系。 例如，它清楚地显示每个“订单”仅与一个菜单关联。  
  
  误解用户的要求经常可以追溯到对单词详细含义的误解。 例如，大多数餐厅对术语“菜单”和“订单”有着相同的理解，但是对于“订单”上的项和“菜单”上的项之间的差异就不那么清晰了。 在与业务利益干系人讨论要求时，提出这些差异非常重要。 类图是一个有用的工具，可帮助你阐明术语和它们之间的关系。  
  
  概念类模型可以形成基本词汇，你的系统业务逻辑可以利用这些词汇进行描述。 但是软件中的类通常会比概念模型更为复杂，因为实现必须考虑性能、分发、灵活性以及其他因素等问题。 一个概念类的多个不同实现经常可以在一个系统中找到。  
  
  例如，可以在系统的不同部件中以及部件之间的不同接口上用 XML、SQL、HTML 和 C# 表示“订单”。 “订单”和“菜单”之间的关联可以通过多种方式表现出来，例如 C# 代码中的引用、数据库中的关系或 XML 中的交叉引用 ID。 尽管存在这些变化，但是概念模型在软件的每个部件中提供的都是重要信息。 该示例中的类图告诉我们，在每个实现中，每个“订单”只有一个“菜单”与之关联。  
  
  绘制需求类图可帮助团队：  
  
- 定义用于讨论用户需求的基本术语，并对其进行标准化。  
  
- 阐明这些术语之间的关系。  
  
  下列主题提供了更多信息：  
  
|了解|读取|  
|--------------------|----------|  
|有关查找要求类的更详细信息|[UML 类图：准则](../modeling/uml-class-diagrams-guidelines.md)|  
|概念类图上的元素|[UML 类图：参考](../modeling/uml-class-diagrams-reference.md)|  
|如何从概念类开发代码|[应用体系结构建模](../modeling/model-your-app-s-architecture.md)|  
  
 在概念类图中，通常在关联上放置箭头来表示可导航性没什么用处。 这是因为此关系图并不表示实现。 关联表示现实世界对象间的关系。 下面的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 扩展将无方向箭头当成默认选择： [示例：UML 域建模功能](http://go.microsoft.com/fwlink/?LinkId=213849)。  
  
##  <a name="BusinessRules"></a> Showing Business Rules  
 业务规则是一个不与特定用例相关联的要求，应在整个系统中进行观察。  
  
 许多业务规则受概念类间关系的约束。 您可以编写这些*静态业务规则*作为与概念类图上的相关类关联的注释。 例如：  
  
 ![附加到 Order 类的注释中的规则。](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")  
  
 *动态业务规则* 对允许的事件序列进行约束。 例如，使用序列或活动图来显示用户必须在登录后才能在你的系统上执行其他操作。  
  
 但是，许多动态规则都可以替换为静态规则，以便更高效、更泛地指定它们。 例如，你可以向概念类模型的类中添加一个 Boolean 属性“已登录”。 将“已登录”添加为登录用例的后置条件，并将其添加为大多数其他用例的前置条件。 这种方法可以让你避免对所有可能的事件序列组合进行定义。 这种方法在你需要向模型添加新用例时，也更加灵活。  
  
 请注意，此处的选择是有关你如何定义要求的方式，与你如何在程序代码中实现要求无关。  
  
 下列主题提供了更多信息：  
  
|了解|读取|  
|--------------------|----------|  
|有关查找和记录静态业务规则的更详细信息|[UML 类图：准则](../modeling/uml-class-diagrams-guidelines.md)|  
|概念类图上的元素|[UML 类图：参考](../modeling/uml-class-diagrams-reference.md)|  
|如何开发符合业务规则的代码|[应用体系结构建模](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Describing Quality of Service Requirements  
 服务质量要求有多个类别。 它们包括以下类型：  
  
- 性能  
  
- 安全性  
  
- 可用性  
  
- 可靠性  
  
- 稳定性  
  
  可以在特定用例的描述中包括其中的一些要求。 其他要求并不特定于用例，并已经非常高效地写入了单独文档。 如果可能，遵守要求模型定所定义的词汇非常有用。 在下面的示例中，请注意，要求中使用的主要词语是参与者、用例和上述插图中的类的标题：  
  
  如果餐厅在顾客订餐时删除了菜单项，则任何引用该菜单项的订单项将显示为红色。  
  
  下列主题提供了更多信息：  
  
|了解|读取|  
|--------------------|----------|  
|有关记录服务要求质量的更详细信息|[定义服务质量要求的准则](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|将其他文档附加到用例|[将用例链接到文档和关系图](../modeling/link-a-use-case-to-documents-and-diagrams.md)|  
|如何开发符合服务质量要求的代码|[应用体系结构建模](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Workflow"></a> 显示用户与系统之间的工作流  
 可以使用活动图来显示不同用例间的工作流。 通过绘制显示用户执行的主要任务（通过系统执行或在系统以外执行的任务）的活动图来开始建立要求模型常常非常有用。  
  
 例如：  
  
 ![包含三个操作和一个循环的活动。](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")  
  
 可以绘制用例图和活动图来显示相同信息的不同视图。  虽然用例图在显示大型活动中嵌套的较小型活动时更具效率，但不会显示工作流。 例如：  
  
 ![以前的操作的用例](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")  
  
 请注意，也可以使用活动图来描述软件内的算法，但在将此关系图用于业务进程时，应关注在系统外可以看到的操作。  
  
 下列主题提供了更多信息：  
  
|了解|读取|  
|--------------------|----------|  
|有关如何定义业务工作流的更多信息|[UML 活动图：准则](../modeling/uml-activity-diagrams-guidelines.md)|  
|活动图中的元素|[UML 活动图：参考](../modeling/uml-activity-diagrams-reference.md)|  
|如何从活动图中开发代码|[应用体系结构建模](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Sequences"></a> 显示用户与系统之间的交互  
 可以使用序列图显示系统和外部参与者之间或系统的各部件与系统之间的消息交换。 这在用例中提供了一个步骤视图，非常清晰地显示了交互序列。 当用例内有多个交互方，且你的系统有 API 时，序列图非常有用。  
  
 例如：  
  
 ![带有 System 和参与者的序列图。](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")  
  
 序列图的一个优点就是可以很方便地看到你所构建的系统收到了什么消息。 若要设计系统，可以将单个系统生命线替换为每个系统组件的独立生命线，然后显示各生命线之间用来响应每个传入消息的交互。  
  
 下列主题提供了更多信息：  
  
|了解|读取|  
|--------------------|----------|  
|有关如何定义交互的更多信息|[UML 序列图：准则](../modeling/uml-sequence-diagrams-guidelines.md)|  
|序列图上的元素|[UML 序列图：参考](../modeling/uml-sequence-diagrams-reference.md)|  
|如何从序列图中开发代码|[应用体系结构建模](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="using-a-model-to-reduce-inconsistencies"></a>使用模型减少不一致  
 创建模型通常可显著减少用户需求方面的不一致和多义性。 不同利益干系人通常对系统工作的业务具有不同的理解。 因此，你的首要任务就是消除客户之间的这些差异。  
  
 你将会发现，当创建模型时自然会出现很多有关业务领域的问题。 通过向用户提出这些问题，将在项目的后续阶段减少更改需求。 下面是一些特定问题，可以先问问自己，如果答案不确定则可以询问业务利益相关者：  
  
- 对于需求模型中的每个类，询问“哪个用例创建此类的实例？” 例如，对于在线订餐服务，你可能会问，“哪个用例创建餐馆菜单类的实例？” 这将导致讨论新餐馆如何向服务注册并提供菜单。 可以询问有关哪个用例创建或更改特性和关联的类似问题。  
  
- 对于需求模型中的每个用例，尝试用类图提供的单词描述每个用例的结果或后置条件。 在用例匹配项前后绘制类实例的草图，对于显示用例的效果通常十分有用。 例如，如果用例后置条件表示“已将菜单项添加到顾客的订单”，则绘制订单和菜单项类实例的草图。 以不同的颜色或在新绘图中显示用例的效果（例如新链接或新对象）。 这通常会导致讨论有关哪些信息在模型中是必需的。 尽管需求类不与实现直接相关，但它们描述系统将需要存储和传输的信息。  
  
- 询问特性和关联的约束，尤其是涉及多个特性或关联的约束。  
  
- 询问有效和无效的用例序列，绘制序列图或活动图以演示这些用例序列。  
  
  通过检查不同关系图提供的视图之间的关系，可以快速理解用户使用的主要概念，并帮助他们理解他们需要从系统中获得什么。 还可以更好地理解利益干系人最不确定的需求。 可以计划在项目的早期阶段至少以简化的形式开发这些功能，从而允许用户体验这些功能。  
  
## <a name="see-also"></a>请参阅  
 [编辑 UML 模型和关系图](../modeling/edit-uml-models-and-diagrams.md)   
 [基于模型开发测试](../modeling/develop-tests-from-a-model.md)   
 [在您的开发过程中使用模型](../modeling/use-models-in-your-development-process.md)   
 [应用程序的体系结构建模](../modeling/model-your-app-s-architecture.md)   
 [示例 VS 扩展： UML 域建模功能](http://go.microsoft.com/fwlink/?LinkId=213849)   
 [示例 VS 扩展： 根据构造型的颜色 UML 元素](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [示例 VS 扩展： UML 元素链接到关系图、 文件和其他元素](http://go.microsoft.com/fwlink/?LinkID=213813)   
 [示例 VS 扩展： 对齐 UML 关系图上形状](http://go.microsoft.com/fwlink/?LinkID=213809)   
 [视频： 业务域建模](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)



