---
title: 代码度量值问题疑难解答
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c20fc0cd975dba4efcf9384d804e7732afecec0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930890"
---
# <a name="troubleshooting-code-metrics-issues"></a>代码度量值问题疑难解答
收集代码度量时，可能会遇到以下的一些问题：

-   [Visual Studio 2010 代码复杂度计算中的更改](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Visual Studio 2010 代码复杂度计算中的更改
 对于相同的函数，在以下情况下，[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中计算的代码复杂度度量可以不同于早期版本的 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 计算的度量：

- 此函数包含一个或多个 catch 块。 在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 以前的版本中，catch 块不包含在计算中。 在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中，每个 catch 块的复杂度均添加到函数的复杂度中。

- 此函数包含 switch（VB 中的 Select Case）语句。 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 和早期版本之间的编译器差异可以为包含失败事例的某些 switch 语句生成不同的 MSIL 代码。

## <a name="see-also"></a>请参阅
 [测量托管代码的复杂性和可维护性](../code-quality/code-metrics-values.md)