---
title: “设置基数”命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93172b8ed16e2520c060671d12ef0ab35960f6ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829403"
---
# <a name="set-radix-command"></a>“设置基数”命令
设置或返回用来显示整数值的数值基数。

## <a name="syntax"></a>语法

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>自变量
 `10` 或 `16` 或 `hex` 或 `dec`

 可选。 指示十进制（10 或 dec）或十六进制（16 或 hex）。 如果省略某个参数，则返回当前基数值。

## <a name="example"></a>示例
 此示例将环境设置为以十六进制格式显示整数值。

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>请参阅

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [“命令”窗口](../../ide/reference/command-window.md)
- [“查找/命令”框](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)