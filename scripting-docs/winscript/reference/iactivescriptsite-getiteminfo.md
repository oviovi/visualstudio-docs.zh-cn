---
title: 'Iactivescriptsite:: Getiteminfo |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc6515d64406870ca10f003d7cea515c49b7d8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095883"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
允许脚本引擎来获取有关与添加的项的信息[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrName`  
 [in]与作为中指定的项关联的名称[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `dwReturnMask`  
 [in]一个位掩码，指定应返回有关项目的哪些信息。 脚本引擎应请求可能的最小信息量，因为一些返回参数 (例如， `ITypeInfo`) 可能需要相当长的时间才能加载或生成。 可以是以下值的组合：  
  
|“值”|含义|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|返回`IUnknown`此项的接口。|  
|SCRIPTINFO_ITYPEINFO|返回`ITypeInfo`此项的接口。|  
  
 `ppunkItem`  
 [out]接收指向的变量的地址`IUnknown`与给定项相关联的接口。 可以使用脚本引擎`IUnknown::QueryInterface`方法来获取`IDispatch`项的接口。 如果此参数会收到 NULL`dwReturnMask`不包括 SCRIPTINFO_IUNKNOWN 值。 此外，收到 NULL，如果没有与项目名称; 关联的对象使用此机制 SCRIPTITEM_CODEONLY 标志设置添加命名的项时创建一个简单的类[iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `ppTypeInfo`  
 [out]接收指向的变量的地址`ITypeInfo`与项关联的接口。 如果此参数会收到 NULL`dwReturnMask`不包括 SCRIPTINFO_ITYPEINFO 值，或类型信息不是可用于此项。 如果类型信息不可用，该对象不能获得事件，并且必须使用实现名称绑定`IDispatch::GetIDsOfNames`方法。 请注意，`ITypeInfo`检索到的接口描述项的组件类 (TKIND_COCLASS)，因为该对象可能支持多个接口和事件接口。 如果项支持`IProvideMultipleTypeInfo`接口，`ITypeInfo`检索到的接口是索引零相同`ITypeInfo`将使用获取的`IProvideMultipleTypeInfo::GetInfoOfIndex`方法。  
  
## <a name="return-value"></a>返回值  
 返回以下值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`TYPE_E_ELEMENTNOTFOUND`|找不到指定名称的项。|  
  
## <a name="remarks"></a>备注  
 此方法检索由信息`dwReturnMask`参数; 这可以提高性能。 例如，如果`ITypeInfo`接口不需要的项，它只需中未指定`dwReturnMask`。  
  
## <a name="see-also"></a>请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)