---
title: __incfsbyte、__incfsword、__incfsdword
ms.date: 11/04/2016
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: f9f0bef89b32e1901c2f6b173baa90153b25a71d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577879"
---
# <a name="incfsbyte-incfsword-incfsdword"></a>__incfsbyte、__incfsword、__incfsdword

**Microsoft 專屬**

相對於開頭的位移所指定的記憶體位置中加入一個值`FS`區段。

## <a name="syntax"></a>語法

```
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>參數

*位移*<br/>
[in]從開頭的位移`FS`。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

## <a name="remarks"></a>備註

這些內建函式僅適用於核心模式，常式僅可作為內建函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__addfsbyte、 \__addfsword， \__addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)<br/>
[__readfsbyte、 \__readfsdword， \__readfsqword， \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[__writefsbyte、 \__writefsdword， \__writefsqword， \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)