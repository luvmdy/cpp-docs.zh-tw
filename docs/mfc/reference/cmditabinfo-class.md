---
title: CMDITabInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: b9b45142d0fb1d53ccecad31ace7ad1a6dd4ee40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524705"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo 類別

`CMDITabInfo`類別用來將參數傳遞給[cmdiframewndex:: Enablemditabbedgroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)方法。 設定這個類別的成員以控制 MDI 索引標籤式群組的行為。

## <a name="syntax"></a>語法

```
class CMDITabInfo
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDITabInfo::Serialize](#serialize)|從封存中讀取或寫入此物件。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|指定是否**關閉**按鈕顯示在 [作用中] 索引標籤的標籤。|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|指定是否要色彩 MDI 索引標籤。|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|指定的索引標籤群組是否顯示快顯功能表，以顯示一份開啟的文件或顯示捲軸按鈕。|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|指定使用者是否可以拖曳來交換的索引標籤的位置。|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|指定的索引標籤是否有一般的框架。|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|指定是否會顯示每個索引標籤的標籤**關閉** 按鈕。|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|指定是否啟用自訂的工具提示。|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|指定是否要在 MDI 索引標籤上顯示圖示。|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|指定每個索引標籤視窗的框線大小。|
|[CMDITabInfo::m_style](#m_style)|指定的索引標籤的樣式。|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|指定的索引標籤的標籤是否位在頂端或底部的頁面。|

## <a name="remarks"></a>備註

這個類別會指定此架構會建立 MDI 索引標籤群組的參數。

## <a name="example"></a>範例

下列範例示範如何設定各種成員變數中的值`CMDITabInfo`類別。

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>需求

**標頭：** afxmdiclientareawnd.h

##  <a name="m_bactivetabclosebutton_"></a>  CMDITabInfo::m_bActiveTabCloseButton;

指定是否**關閉**按鈕顯示在 [作用中] 索引標籤的標籤。

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>備註

如果為 TRUE，將會顯示 作用中 索引標籤的標籤**關閉** 按鈕。 **關閉**按鈕會移除索引標籤區域的右上角。 否則，不會顯示 作用中 索引標籤的標籤**關閉** 按鈕。 **關閉**按鈕會出現在索引標籤區域的右上角。

##  <a name="m_bautocolor"></a>  CMDITabInfo::m_bAutoColor

指定每個 MDI 索引標籤是否有它自己的色彩。

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>備註

如果為 TRUE，每個索引標籤會有自己的色彩。 色彩是由 MFC 程式庫管理。 否則，索引標籤會以白色顯示。 預設值為 FALSE。

##  <a name="m_bdocumentmenu"></a>  CMDITabInfo::m_bDocumentMenu

指定是否每個索引標籤會顯示快顯功能表會顯示開啟的文件索引標籤區域右側的清單。

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>備註

如果為 TRUE，每個索引標籤式視窗會顯示快顯功能表會顯示在右邊緣的索引標籤區域中，開啟的文件的清單否則 索引標籤視窗會顯示捲軸按鈕 索引標籤 區域右邊緣。 預設值為 FALSE。

##  <a name="m_benabletabswap"></a>  CMDITabInfo::m_bEnableTabSwap

指定使用者是否可以拖曳來交換的索引標籤的位置。

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>備註

如果為 TRUE，使用者可以拖曳索引標籤，變更索引標籤位置。 否則，使用者無法變更索引標籤位置。 預設值為 TRUE。

##  <a name="m_bflatframe"></a>  CMDITabInfo::m_bFlatFrame

指定每個索引標籤視窗是否有一般的框架。

```
BOOL m_bFlatFrame;
```

##  <a name="m_btabclosebutton"></a>  CMDITabInfo::m_bTabCloseButton

指定是否要顯示每個索引標籤視窗**關閉** 按鈕。

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>備註

如果為 TRUE，就會顯示每個索引標籤視窗**關閉** 索引標籤的右邊緣的按鈕。否則，請**關閉**按鈕不會顯示。 預設值為 TRUE。

##  <a name="m_btabcustomtooltips"></a>  CMDITabInfo::m_bTabCustomTooltips

指定是否在索引標籤顯示工具提示。

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>備註

如果為 TRUE，應用程式會傳送回主框架 AFX_WM_ON_GET_TAB_TOOLTIP 訊息。 您可以使用 ON_REGISTERED_MESSAGE 巨集來處理此訊息。

##  <a name="m_btabicons"></a>  CMDITabInfo::m_bTabIcons

指定是否要在 MDI 索引標籤上顯示圖示。

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>備註

如果為 TRUE，則會在每個 MDI 索引標籤上顯示圖示。否則，圖示不會顯示在索引標籤上。 預設值為 FALSE。

##  <a name="m_ntabbordersize"></a>  CMDITabInfo::m_nTabBorderSize

指定的框線大小，單位為像素，每個索引標籤視窗。

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>備註

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)傳回的預設值。

##  <a name="m_style"></a>  CMDITabInfo::m_style

指定的索引標籤的樣式。

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>備註

指定其中一個索引標籤的下列樣式：

|||
|-|-|
|STYLE_3D|3D 樣式。  |
|STYLE_3D_ONENOTE|Microsoft OneNote 樣式。  |
|STYLE_3D_VS2005|Microsoft Visual Studio 2005 樣式。  |
|STYLE_3D_SCROLLED|使用矩形的索引標籤的 3D 樣式。  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|使用共用的水平捲軸的平面樣式。  |
|STYLE_3D_ROUNDED_SCROLL|使用 round 索引標籤的 3D 樣式。  |

##  <a name="m_tablocation"></a>  CMDITabInfo::m_tabLocation

指定的索引標籤的標籤是否位在頂端或底部的頁面。

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>備註

適用於下列位置旗標的一個索引標籤：

- LOCATION_BOTTOM： 索引標籤的標籤會位於頁面底部。

- LOCATION_TOP： 索引標籤的標籤會位於頁面頂端

##  <a name="serialize"></a>  CMDITabInfo::Serialize

讀取或寫入此物件從封存至封存。

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
[in]A [CArchive 類別](../../mfc/reference/carchive-class.md)来序列化的物件。

## <a name="see-also"></a>另請參閱

[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI 索引標籤式群組](../../mfc/mdi-tabbed-groups.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
