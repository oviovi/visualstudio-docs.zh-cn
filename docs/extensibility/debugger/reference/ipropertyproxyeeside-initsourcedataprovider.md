---
title: IPropertyProxyEESide::InitSourceDataProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 652eaf5525de404fe3107449f56ad714b1b827cf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937408"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
初始化此对象的源数据并返回一个包含初始数据的对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dataOut`  
 [out]返回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)对象  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法会执行任何所需初始化对象，以便它可以返回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)上对象的数据的接口。 这允许查看和，如果允许，更改类型可视化工具对象的数据。  
  
## <a name="see-also"></a>请参阅  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)