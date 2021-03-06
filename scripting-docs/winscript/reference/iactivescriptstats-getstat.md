---
title: IActiveScriptStats::GetStat |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d00c438f0fe03566dfb7efb93645cad02dc7477
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095389"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
返回一个标准脚本统计信息。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>参数  
 `stid`  
 [in]指定要返回的统计信息。 必须为值：  
  
|返回的常量|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|返回自启动的脚本或已重置统计信息以来执行的语句数。|  
  
 `pluHi`  
 [out]表示统计信息的 64 位无符号整数的高 32 位。  
  
 `pluLo`  
 [out]表示统计信息的 64 位无符号整数的低 32 位。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括但不限于以下表中的值。  
  
|“值”|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法返回一个标准脚本统计信息。  
  
## <a name="see-also"></a>请参阅  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats 接口](../../winscript/reference/iactivescriptstats-interface.md)