---
title: __readfsbyte、__readfsdword、__readfsqword、__readfsword
ms.date: 11/04/2016
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: e5610fcd9be369718875f2f7a7bd358e7c2b07dc
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327677"
---
# <a name="readfsbyte-readfsdword-readfsqword-readfsword"></a>__readfsbyte、__readfsdword、__readfsqword、__readfsword

**Microsoft 專屬**

讀取記憶體從相對於 FS 區段開頭的位移所指定的位置。

## <a name="syntax"></a>語法

```
unsigned char __readfsbyte(
   unsigned long Offset
);
unsigned short __readfsword(
   unsigned long Offset
);
unsigned long __readfsdword(
   unsigned long Offset
);
unsigned __int64 __readfsqword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>參數

*位移*<br/>
[in]從開頭的位移`FS`來讀取。

## <a name="return-value"></a>傳回值

記憶體中的位元組、 word、 doubleword 或 （如下所呼叫的函式的名稱） 的 quadword 內容位於位置`FS:[Offset]`。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

這些常式都僅有內建函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__writefsbyte、 \__writefsdword， \__writefsqword， \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)