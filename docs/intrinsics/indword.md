---
title: __indword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: f4b37247093da14c8d5e8fed69b01265d3fed2ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599806"
---
# <a name="indword"></a>__indword

**Microsoft 專屬**

從指定的連接埠使用讀取資料的一個雙精度浮點數字`in`指令。

## <a name="syntax"></a>語法

```
unsigned long __indword(
   unsigned short Port
);
```

#### <a name="parameters"></a>參數

*連接埠*<br/>
[in]要讀取的連接埠。

## <a name="return-value"></a>傳回值

從連接埠，讀取這個字。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__indword`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)