---
title: 预期) 中的正则表达式 (JavaScript) |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c344105010e406ef4936fdcca58baffbd610088
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802337"
---
# <a name="expected--in-regular-expression-javascript"></a>正则表达式中应有“)”(JavaScript)
试图创建正则表达式捕获、 断言或组，但不是包括右括号。 括号的正则表达式中具有多个用途。 首先，它们用来捕获子表达式，若要指定断言，或将模式组合在一起，以便可以将项视为单个单元通过 *，+、？、，等等。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   添加最右侧的右括号。  
  
    > [!NOTE]
    >  如果您希望匹配单个括号，对其进行转义反斜杠- \\(-，以便它不被视为特殊字符的[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](https://msdn.microsoft.com/library/1400241x)