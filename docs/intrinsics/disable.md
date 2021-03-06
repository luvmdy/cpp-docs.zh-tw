---
title: _disable
ms.date: 11/04/2016
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 64e7031ab578632322dfd5c73eb81e0750c1e0b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587807"
---
# <a name="disable"></a>_disable

**Microsoft 專屬**

停用中斷。

## <a name="syntax"></a>語法

```
void _disable(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_disable`|x86、 x64、 ARM|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`_disable` 指示處理器清除中斷旗標。 在 x86 系統中，這個函式會產生清除中斷旗標 (`cli`) 指令。

這個函式只適用於核心模式。 如果在使用者模式中使用，會在執行階段擲回有權限指令例外狀況。

在 ARM 平台上，此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)