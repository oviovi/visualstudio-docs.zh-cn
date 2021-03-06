---
title: FeatureProperties 元素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7843d8a8ee9fc21c546c8cfca57cfef63cd4015
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955667"
---
# <a name="featureproperties-element"></a>FeatureProperties 元素
  部署到 SharePoint 时，包含与某个功能的属性值的集合。 将功能部署后，你可以在代码中访问的属性值。  
  
## <a name="syntax"></a>语法  
  
```xml  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素
  
|元素|描述|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|可选元素。<br /><br /> 表示键/值格式中的自定义属性。|  
  
### <a name="parent-elements"></a>父元素
  
|元素|描述|  
|-------------|-----------------|  
|[项目项](../sharepoint/projectitem-element.md)|表示 SharePoint 项目项。 此元素的必需的根元素的`.spdata`文件。|  
  
## <a name="remarks"></a>备注  
 功能属性的详细信息，请参阅[提供在项目项中的打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>元素信息
  
|元素|描述|  
|-------------|-----------------|  
|**命名空间**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**可以为空**|否|  
  
## <a name="see-also"></a>请参阅
 [SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供在项目项中的打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
