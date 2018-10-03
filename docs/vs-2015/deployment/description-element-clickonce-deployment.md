---
title: "&lt;description&gt;要素 (ClickOnce 配置) |Microsoft Docs'"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 473ebf814ab65c34ee99cab0cf2cc239e0d013eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468780"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;说明&gt;元素 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[&lt;描述&gt;元素 （ClickOnce 部署）](https://docs.microsoft.com/visualstudio/deployment/description-element-clickonce-deployment)。  
  
标识用于创建 shell 表示应用程序信息和一个**添加或删除程序**控制面板中的项。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `description` 元素是必需的，它位于 `urn:schemas-microsoft-com:asm.v1` 命名空间中。 它不包含任何子元素，并具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`publisher`|必须的。 标识用于在 Windows 中的图标位置的公司名称**启动**菜单并**添加或删除程序**控件面板中的部署配置进行安装时的项。|  
|`product`|必须的。 标识完整的产品名称。 使用作为安装在 Windows 中的图标的头衔**启动**菜单。|  
|`suiteName`|可选。 标识的子文件夹中`publisher`在 Windows 中的文件夹**启动**菜单。|  
|`supportUrl`|可选。 指定所示的支持 URL**添加或删除程序**控制面板中的项。 在 Windows 中的应用程序支持还为创建此 URL 的快捷方式**启动**菜单中，部署配置为安装时。|  
  
## <a name="remarks"></a>备注  
 Description 元素中所有的部署配置需要。  
  
## <a name="example"></a>示例  
 下面的代码示例演示`description`中的元素[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署清单。 此代码示例是为提供一个更大示例的一部分[ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)


