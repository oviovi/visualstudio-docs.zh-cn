---
title: SCRIPTPROP_HOSTKEEPALIVE 属性 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c8918e277fa9c7183e6d46a4853824a74fa4548
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087368"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE 属性
用于指定应保留脚本引擎完全正常运行，如果有未完成的引用。  
  
 使用[IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md)若要将此属性设置为`true`。 如果此属性设置为`true`，脚本引擎保持完全正常运行，只要没有至少一个未完成引用到脚本引擎本身或`IDispatch`到通过使用脚本创建的 JavaScript 对象的指针引擎。 当此属性设置为`true`，你应未显式关闭或通过使用重置脚本引擎[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)或[iactivescript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md)方法。 对脚本对象的最后一个引用的版本会关闭脚本引擎。  
  
## <a name="syntax"></a>语法  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>要求  
 此属性只 activscp.idl 随一起安装的版本中将出现[!INCLUDE[win8](../../javascript/includes/win8-md.md)]，使用 Internet Explorer 8 上的 KB 2707082 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]，或使用 Internet Explorer 9 上的 KB 2722913[!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]或[!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]。