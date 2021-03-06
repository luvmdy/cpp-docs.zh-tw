---
title: 資料對齊
ms.date: 11/04/2016
f1_keywords:
- data.alignment
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
ms.openlocfilehash: 7d835545bdc1f94de56846f35d510927c06c2560
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520275"
---
# <a name="data-alignment"></a>資料對齊

下列 C 執行階段函式支援資料對齊。

## <a name="data-alignment-routines"></a>資料對齊常式

|常式傳回的值|使用|
|-------------|---------|
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|釋放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊。|
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|釋放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊 (僅限偵錯)。|
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|針對指定的對齊界限配置記憶體。|
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|使用額外空間為偵錯標頭及覆寫緩衝區，依指定的對齊界限配置記憶體 (僅限偵錯版本)。|
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|傳回堆積中所配置的記憶體區塊大小。|
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|傳回堆積中所配置的記憶體區塊大小 (僅限偵錯版本)。|
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|針對指定的對齊界限配置記憶體。|
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|在指定的對齊界限上配置記憶體 (僅限偵錯版本)。|
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小。|
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小 (僅限偵錯版本)。|
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0。|
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0 (僅限偵錯版本)。|
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小。|
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小 (僅限偵錯版本)。|
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0。|
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0 (僅限偵錯版本)。|

## <a name="see-also"></a>請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>