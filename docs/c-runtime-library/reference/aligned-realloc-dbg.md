---
title: _aligned_realloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_realloc_dbg
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- aligned_realloc_dbg
- _aligned_realloc_dbg
helpviewer_keywords:
- _aligned_realloc_dbg function
- aligned_realloc_dbg function
ms.assetid: 8aede920-991e-44cd-867f-83dc2165db47
ms.openlocfilehash: 2a261b3e578bef5464bbfda8528ffd8b491acb23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545947"
---
# <a name="alignedreallocdbg"></a>_aligned_realloc_dbg

變更使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 所配置的記憶體區塊大小 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void * _aligned_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
目前記憶體區塊指標。

*size*<br/>
要求的記憶體配置的大小。

*對齊方式*<br/>
對齊值，必須是 2 的整數冪。

*filename*<br/>
要求的原始程式檔的名稱指標**realloc**作業或**NULL**。

*linenumber*<br/>
原始程式檔中的行號所在**realloc**要求作業，或**NULL**。

## <a name="return-value"></a>傳回值

**_aligned_realloc_dbg**傳回重新配置後 （且可能有移動） 記憶體區塊的 void 指標。 傳回值是**NULL**如果大小為零，而且緩衝區引數不是**NULL**，或如果沒有足夠的可用記憶體將區塊展開指定的大小。 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。

重新配置記憶體並變更區塊的對齊是不對的。

## <a name="remarks"></a>備註

**_aligned_realloc_dbg**是偵錯版本[_aligned_realloc](aligned-realloc.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，每次呼叫 **_aligned_realloc_dbg**的呼叫會降低 **_aligned_realloc**。 兩者 **_aligned_realloc**並 **_aligned_realloc_dbg**重新配置基底堆積中的記憶體區塊，但 **_aligned_realloc_dbg**容納數種偵錯功能： 以測試遺漏，來追蹤特定配置類型的區塊類型參數的區塊使用者部分任一端使用緩衝區和*檔名*/*linenumber*若要判斷配置要求來源的資訊。

**_aligned_realloc_dbg**重新配置比要求稍微多一些的空間與指定的記憶體區塊*newSize*。 *newSize*可能大於或小於原本配置的記憶體區塊的大小。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 重新配置可能會導致將原始記憶體區塊移到堆積中的不同位置，也可能會變更記憶體區塊的大小。 若記憶體區塊已移動，則會覆寫原始區塊的內容。

**_aligned_realloc_dbg**設定**errno**要**ENOMEM**若記憶體配置失敗或需要的記憶體數量 （包含先前所述的額外負荷） 超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

此外， **_aligned_realloc_dbg**會驗證其參數。 如果*對齊*不是乘冪為 2，此函式會叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則此函數會傳回**NULL**並設定**errno**來**EINVAL**。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_realloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
