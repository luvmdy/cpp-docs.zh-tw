---
title: RGNDATA 結構
ms.date: 11/04/2016
f1_keywords:
- RGNDATA
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
ms.openlocfilehash: d6ee25b490aa5c7055b4e8ccf63939fbdd8dd4ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638135"
---
# <a name="rgndata-structure"></a>RGNDATA 結構

`RGNDATA` 結構包含標頭和組成區域的矩形陣列。 這些由上而下由左至右排序的矩形不會重疊。

## <a name="syntax"></a>語法

```
typedef struct _RGNDATA { /* rgnd */
    RGNDATAHEADER rdh;
    char Buffer[1];
} RGNDATA;
```

#### <a name="parameters"></a>參數

*rdh*<br/>
指定[RGNDATAHEADER](/windows/desktop/api/wingdi/ns-wingdi-_rgndataheader)結構。 （如需有關此結構的詳細資訊，請參閱 Windows SDK）。這個結構的成員指定區域類型 (它是否為矩形或梯形)、組成區域的矩形數量和包含矩形結構的緩衝區大小等等。

*Buffer*<br/>
指定包含任意大小的緩衝區[RECT](../../mfc/reference/rect-structure1.md)組成區域的結構。

## <a name="requirements"></a>需求

**標頭：** wingdi.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)<br/>
[CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

