---
title: 代码映射速度较慢
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: 5a7892e8e0bc347c4a22dd1a2ae2ee4b01882d6c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905054"
---
# <a name="improve-performance-for-code-maps"></a>提高代码图的性能

在首次生成代码图时，Visual Studio 会将其找到的所有依赖关系都编入索引中。 此过程可能需要一些时间，尤其是对于大型解决方案，但会提高之后的性能。 如果更改了代码，Visual Studio 只会将已更新的代码重新编入索引。 若要尽量减少完成呈现地图所需的时间，请考虑以下建议：

- [仅映射你感兴趣的依赖关系。](#create-a-code-map-to-see-specific-dependencies)

- 在生成整个解决方案的代码图之前，缩小解决方案范围。

- 通过选择关闭自动生成解决方案**跳过生成**代码图工具栏上。

- 关闭通过选择自动添加父项**包括父级**代码图工具栏上。

   ![跳过“生成和包括父项”按钮](../modeling/media/codemapsfilterskipbuildicons.png)

- 直接编辑代码图文件，以删除不需要的节点和链接。 更改代码图不会影响基础代码。 请参阅 [通过编辑 DGML 文件自定义代码图](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。

可能需要更多时间来创建代码图或将项添加到从地图**解决方案资源管理器**的项目项时**复制到输出目录**属性设置为**始终复制**。 若要提高性能，请将此属性更改为“如果较新则复制”  或 `PreserveNewest`。 请参阅[增量生成](../msbuild/incremental-builds.md)。

已完成代码图显示仅对已成功生成的代码的依赖项。 如果某些组件出现生成错误，这些错误会出现在代码图上。 在基于代码图做出体系结构决策时，请确保组件实际生成并且具有依赖项。