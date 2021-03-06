---
title: 查找内存泄漏的 CRT 库 |Microsoft Docs
ms.custom: ''
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b797e8c8068523b4c782c4d7f02a3853c1d37d1
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050100"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>查找内存泄漏 CRT 库

在 C/c + + 应用程序中最难捉摸也硬检测 bug 都是内存泄漏。 内存泄漏未能正确释放以前分配的内存中的结果。 少量内存泄漏不开始时，会注意到，但随着时间的推移可能导致性能不佳范围到发生故障时应用程序内存不足的症状。 将占用所有可用内存可能会导致其他应用崩溃的泄漏应用，创建不清楚哪些应用程序负责。 即使无害的内存泄漏可能表示应更正其他问题。  

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]调试器和 C 运行时库 (CRT) 可以帮助你检测和识别内存泄漏。  

## <a name="enable-memory-leak-detection"></a>启用内存泄漏检测  

检测内存泄漏是 C/c + + 调试器和 C 运行时库 (CRT) 的主要工具调试堆函数。  

若要启用调试堆的所有函数，在 c + + 程序中，按以下顺序包含以下语句：  

```cpp
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  

`#define` 语句将 CRT 堆函数的基础版本映射到对应的调试版本。 如果您忽略`#define`语句，为内存泄漏转储[不够详尽](#interpret-the-memory-leak-report)。  

包括*crtdbg.h*映射`malloc`并`free`到其调试版本中，函数[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)并[_free_dbg](/cpp/c-runtime-library/reference/free-dbg)，它们将跟踪内存分配和解除分配。 此映射只在包含 `_DEBUG`的调试版本中发生。 发布版本使用普通的 `malloc` 和 `free` 函数。  

通过使用上面的语句启用调试堆函数后，将调用[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)之前应用程序退出时显示的内存泄漏报告的应用程序退出点。  

```cpp
_CrtDumpMemoryLeaks();  
```  

如果您的应用程序有多个退出，无需手动设置`_CrtDumpMemoryLeaks`在每个退出点。 若要使自动调用`_CrtDumpMemoryLeaks`在每个退出点，将调用`_CrtSetDbgFlag`使用如下所示的位域对应用程序的开头：

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  

默认情况下， `_CrtDumpMemoryLeaks` 将内存泄漏报告输出到  “输出”窗口的  “调试”窗格中。 如果使用库，该库可能会将输出重置到另一位置。 

可以使用`_CrtSetReportMode`该报告重定向到其他位置，或返回到**输出**窗口如下所示：  

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  

## <a name="interpret-the-memory-leak-report"></a>解释内存泄漏报告  

如果应用没有定义`_CRTDBG_MAP_ALLOC`， [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)显示如下所示的内存泄漏报告：  

```cmd
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

如果您的应用程序定义`_CRTDBG_MAP_ALLOC`，内存泄漏报告如下所示：  

```cmd
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

第二个报表显示首次分配泄漏的内存的文件名和行号。  

该值指示是否定义`_CRTDBG_MAP_ALLOC`，内存泄漏报告将显示：  

- 内存分配编号，即`18`在示例  
- 块类型，`normal`在示例中。  
- 十六进制内存位置`0x00780E80`在示例中。  
- 块的大小`64 bytes`在示例中。  
- 块中前 16 个字节的数据（十六进制形式）。  

内存块类型*正常*，*客户端*，或*CRT*。  “普通块”是由程序分配的普通内存。  “客户端块”是由 MFC 程序用于需要析构函数的对象的特殊类型内存块。 MFC `new` 运算符根据正在创建的对象的需要创建普通块或客户端块。 

 “CRT 块”是由 CRT 库为自己使用而分配的内存块。 CRT 库处理这些块，解除分配，因此 CRT 块不会显示在内存泄漏报告中，除非使用 CRT 库的严重问题。  

内存泄漏报告中绝对不会出现另外两个内存块类型。 一个*释放的块*是已释放，以便根据定义不会泄漏的内存。 *忽略块*是已显式标记要从内存泄漏报告中排除。  

以前的技术确定内存泄漏的内存分配使用标准 CRT`malloc`函数。 如果您的程序分配内存使用 c + +`new`运算符，但是，你可能只能看到文件名和行号位置`operator new`调用`_malloc_dbg`内存泄漏报告中。 若要创建更有用的内存泄漏报告，可以编写如下所示来报告进行分配的行的宏： 

```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  

现在可以替换`new`运算符使用`DBG_NEW`在代码中的宏。 在调试版本中，`DBG_NEW`使用的全局重载`operator new`采用附加参数的块类型、 文件和行号。 重载`new`调用`_malloc_dbg`记录的额外信息。 内存泄漏报告显示文件名和行号泄漏的对象的分配位置。 发行版本仍然使用默认值`new`。 下面是技术的示例：  

```cpp  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  

在 Visual Studio 中运行此代码时调试器中调用`_CrtDumpMemoryLeaks`生成中的报表**输出**看起来类似于的窗口：  

```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  

此输出的第 20 行已泄漏的分配的报告*debug_new.cpp*。  

>[!NOTE]
>我们不建议创建一个名为的预处理器宏`new`，或任何其他语言关键字。 

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>内存分配编号上设置断点  

如果分配了泄漏内存块，内存分配编号会通知你。 块内存分配编号为 18，例如，是内存的应用程序运行期间分配的第 18 块。 CRT 报告包含运行期间，其中包括 CRT 库和 MFC 等其他库由分配所有内存块分配情况。 因此，内存分配块编号 18 可能不是分配你的代码的第 18 内存块。 

可以使用分配编号在内存分配位置设置断点。  

**若要设置使用监视窗口的内存分配断点：**  

1. 您的应用程序的起点附近设置断点并开始调试。  
   
1. 当应用程序会在断点处暂停时，打开**Watch**通过选择窗口**调试** > **Windows** > **监视 1**(或**观看 2**，**观看 3**，或**观看 4**)。  
   
1. 在中**Watch**窗口中，键入`_crtBreakAlloc`中**名称**列。  
   
   如果您使用的多线程的 DLL 版本的 CRT 库 （/MD 选项），添加上下文运算符： `{,,ucrtbased.dll}_crtBreakAlloc`  
   
1. 按 **Enter**。  
   
   调试器将计算调用，并将结果放入  “值”列。 此值将为**为-1**如果你尚未在内存分配上设置任何断点。  
   
1. 在中**值**列中，值替换为要调试程序执行中断的内存分配的分配编号。  

内存分配编号上设置断点后，继续调试。 请确保在相同条件下运行，因此不会更改的内存分配编号。 当应用程序在指定的内存分配处中断时，使用**调用堆栈**窗口和其他调试器窗口来确定分配内存时的情况。 然后，可以继续执行程序以观察对象会发生什么情况，并确定为什么它不正确释放。  

在对象上设置数据断点可能也有帮助。 有关详细信息，请参阅[使用断点](../debugger/using-breakpoints.md)。  

你也可以在代码中设置内存分配断点。 您可以设置：  

```cpp
_crtBreakAlloc = 18;  
```  

 或：  

```cpp
_CrtSetBreakAlloc(18);  
```  

## <a name="compare-memory-states"></a>比较内存状态  
 定位内存泄漏的另一种技术涉及在关键点对应用程序的内存状态拍快照。 若要在应用程序中给定点处的内存状态的快照，创建`_CrtMemState`结构并将其传递给`_CrtMemCheckpoint`函数。 

```cpp
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
```  

`_CrtMemCheckpoint`函数填充在该结构的当前内存状态的快照。  

若要输出的内容`_CrtMemState`结构，请将传递到结构`_ CrtMemDumpStatistics`函数：  

```cpp
_CrtMemDumpStatistics( &s1 );  
```  

`_ CrtMemDumpStatistics` 输出内存状态转储，如下所示：  

```cmd
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
```  

若要确定在某个代码部分中是否发生了内存泄漏，可以对这部分之前和之后的内存状态拍快照，然后使用 `_ CrtMemDifference` 比较两个状态：  

```cpp
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  

if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  

`_CrtMemDifference` 比较内存状态`s1`并`s2`，并返回结果中的 (`s3`)，它是之间的差异`s1`和`s2`。  

查找内存泄漏的一项技术开始上来`_CrtMemCheckpoint`的开头和结尾的您的应用程序，然后使用在调用`_CrtMemDifference`可以比较的结果。 如果`_CrtMemDifference`显示了内存泄漏，可以添加更多`_CrtMemCheckpoint`调用来划分程序使用二进制搜索，直到你已隔离找到泄漏源。  

## <a name="false-positives"></a>误报  
 `_CrtDumpMemoryLeaks` 如果库将内部分配标记为普通块而不是 CRT 块或客户端块可能给出错误地指示内存泄漏。 在这种情况下， `_CrtDumpMemoryLeaks` 无法区分用户分配和内部库分配。 如果在 `_CrtDumpMemoryLeaks`调用点之后运行库分配的全局析构函数，则每个内部库分配都会报告为内存泄漏。 版本早于可能会导致 Visual Studio.NET 的标准模板库`_CrtDumpMemoryLeaks`以报告此类的假正值。  

## <a name="see-also"></a>请参阅  
 [CRT 调试堆详细信息](../debugger/crt-debug-heap-details.md)   
 [调试器安全](../debugger/debugger-security.md)   
 [调试本机代码](../debugger/debugging-native-code.md)
