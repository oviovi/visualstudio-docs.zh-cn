---
title: CreateExpInstance 实用工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39aed4f3c02b1467f2fdf975d6443923acd018f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961097"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 实用工具
使用**CreateExpInstance**实用程序来创建、 重置，或删除 Visual Studio 的实验实例。 可以使用实验实例来调试和测试 Visual Studio 扩展，而无需更改基础产品。  
  
## <a name="syntax"></a>语法  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
## <a name="parameters"></a>参数  
 **/ 创建**创建实验实例。  
  
 **/ 重置**  
 删除实验实例，然后创建一个新。  
  
 **/Clean**  
 删除实验实例。  
  
 **/ VSInstance**  
 包含要复制的基本 Visual Studio 实例的目录的名称。  
  
 **/ RootSuffix**  
 要追加到实验实例目录的名称的后缀。  
  
## <a name="remarks"></a>备注  
 当您正在从事 Visual Studio 扩展时，可以按 f5 键以打开默认实验实例，并安装当前的扩展。 如果没有实验实例不可用，Visual Studio 将创建一个具有默认设置。  
  
 实验实例的默认位置取决于 Visual Studio 版本号。 例如，对于 Visual Studio 2015 中，位置是 *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*。 中的目录位置的所有文件被都视为该实例的一部分。 将由 Visual Studio 加载任何其他实验实例，除非目录名称已更改为默认位置。  
  
 在打开的实验实例时，visual Studio 不访问系统注册表。 这不同于早期版本的 Visual Studio 中，使用注册表配置单元的实验性版本。  
  
 **CreateExpInstance**实用程序替换**VsRegEx**实用程序。  
  
 以下示例重置默认的 Visual Studio 的实验实例：  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>请参阅  
 [VSPackage](../../extensibility/internals/vspackages.md)