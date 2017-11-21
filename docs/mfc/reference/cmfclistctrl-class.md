---
title: "CMFCListCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
dev_langs: C++
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c8b4172167a60425603bb25acff5670a5901c307
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 類別
`CMFCListCtrl`類別會擴充功能的[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)類別所支援的進階標頭控制項功能[CMFCHeaderCtrl 類別](../../mfc/reference/cmfcheaderctrl-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|可讓您將已排序的資料行具有不同的背景色彩標示。|  
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|可讓多個排序模式。|  
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|傳回加底線的標頭控制項的參考。|  
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|檢查清單控制項是否處於多重排序模式。|  
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|它必須比較兩個清單控制項項目時由架構呼叫。|  
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|必須先決定個別資料格的背景色彩時由架構呼叫。|  
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|它必須取得要繪製的儲存格的字型時由架構呼叫。|  
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|必須先決定個別資料格的文字色彩時由架構呼叫。|  
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|從已排序的資料行的清單中移除資料行排序。|  
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|設定目前的已排序資料行和排序順序。|  
|[CMFCListCtrl::Sort](#sort)|排序清單控制項。|  
  
## <a name="remarks"></a>備註  
 `CMFCListCtrl`提供兩個增強功能[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)類別。 首先，它表示資料行排序可用的選項自動標頭上繪製排序箭號。 第二，它支援在同一時間排序多個資料行的資料。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCListCtrl`類別。 此範例示範如何建立清單控制項、 插入資料行插入項目、 設定項目，文字及設定清單控制項的字型。 此程式碼片段是部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxlistctrl.h  
  
##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn  
 標記已排序的資料行具有不同的背景色彩。  
  
```  
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMark`  
 布林值參數，決定是否要啟用不同的背景色彩。  
  
 [in] `bRedraw`  
 布林值參數，決定是否要立即重繪控制項。  
  
### <a name="remarks"></a>備註  
 `EnableMarkSortedColumn`使用方法`CDrawingManager::PixelAlpha`來計算要使用的色彩排序資料行。 挑選色彩根據一般的背景色彩。  
  
##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort  
 啟用多個資料行排序的清單控制項中的資料列。  
  
```  
void EnableMultipleSort(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值，指定是否要啟用多個資料行排序模式。  
  
### <a name="remarks"></a>備註  
 當您啟用排序依據多個資料行時，資料行沒有階層。 資料列會排序依據的主要資料行。 任何對等的值然後會依每個後續的資料行，根據優先順序排序。  
  
##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl  
 傳回至標題控制項的參考。  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>傳回值  
 參考的基礎[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)物件。  
  
### <a name="remarks"></a>備註  
 標頭之控制項的控制項清單是包含資料行標題的視窗。 它通常位於正上方之資料行。  
  
##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort  
 檢查是否在清單控制項目前支援多個資料行排序。  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果清單控制項支援多個排序;`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 當[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)支援多個排序時，使用者可以排序多個資料行清單控制項中的資料。 若要啟用多個排序，請呼叫[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)。  
  
##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems  
 架構會呼叫這個方法時，它會比較兩個項目。  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>參數  
 [in] `lParam1`  
 要比較的第一個項目。  
  
 [in] `lParam2`  
 要比較的第二個項目。  
  
 [in] `iColumn`  
 這個方法會排序資料行的索引。  
  
### <a name="return-value"></a>傳回值  
 整數，表示兩個項目相對位置。 負數值表示第一個項目之前，第二個，正值表示第一個項目應該遵循第二個，而且零則表示兩個項目相等。  
  
### <a name="remarks"></a>備註  
 預設實作一定會傳回 0。 您必須覆寫此函式可提供排序演算法。  
  
##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor  
 架構會呼叫這個方法時必須判斷個別的資料格的背景色彩。  
  
```  
virtual COLORREF OnGetCellBkColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>參數  
 [in] `nRow`  
 有問題的儲存格的資料列。  
  
 [in] `nColumn`  
 有問題的儲存格的資料行。  
  
### <a name="return-value"></a>傳回值  
 A`COLOREF`值，指定儲存格的背景色彩。  
  
### <a name="remarks"></a>備註  
 預設實作`OnGetCellBkColor`不使用提供的輸入的參數，並改為只需呼叫`GetBkColor`。 因此，根據預設，整份清單控制項會有相同的背景色彩。 您可以覆寫`OnGetCellBkColor`標記以個別的背景色彩的個別資料格衍生類別中。  
  
##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont  
 當它取得個別資料格的字型，架構會呼叫這個方法。  
  
```  
virtual HFONT OnGetCellFont(
    int nRow,  
    int nColumn,  
    DWORD dwData = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `nRow`  
 有問題的儲存格的資料列。  
  
 [in] `nColumn`  
 有問題的儲存格的資料行。  
  
 [in] `dwData`  
 使用者定義的資料。 預設實作不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 適用於目前的儲存格的字型控制代碼。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法會傳回`NULL`。 所有清單控制項中的資料格都有相同的字型。 覆寫這個方法，以針對不同的儲存格提供不同的字型。  
  
##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor  
 架構會呼叫這個方法時必須判斷個別的資料格的文字色彩。  
  
```  
virtual COLORREF OnGetCellTextColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>參數  
 [in] `nRow`  
 有問題的儲存格的資料列。  
  
 [in] `nColumn`  
 有問題的儲存格的資料行。  
  
### <a name="return-value"></a>傳回值  
 A`COLOREF`值，指定儲存格的文字色彩。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法會呼叫`GetTextColor`不論輸入參數。 整份清單控制項會有相同的文字色彩。 您可以覆寫`OnGetCellTextColor`標記以個別的文字色彩的個別資料格衍生類別中。  
  
##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn  
 從已排序的資料行的清單中移除資料行排序。  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>參數  
 [in] `iColumn`  
 若要移除資料行。  
  
### <a name="remarks"></a>備註  
 這個方法會移除標題控制項中排序資料行。 它會呼叫[CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)。  
  
##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn  
 設定目前的已排序資料行和排序順序。  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `iColumn`  
 若要排序資料行。  
  
 [in] `bAscending`  
 布林值，指定排序次序。  
  
 [in] `bAdd`  
 布林值，指定方法是否會將所指定的資料行`iColumn`排序資料行的清單。  
  
### <a name="remarks"></a>備註  
 這個方法會輸入的參數傳遞至標題控制項使用的方法[CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)。  
  
##  <a name="sort"></a>CMFCListCtrl::Sort  
 排序清單控制項。  
  
```  
virtual void Sort(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `iColumn`  
 若要排序資料行。  
  
 [in] `bAscending`  
 布林值，指定排序次序。  
  
 [in] `bAdd`  
 布林值，指定是否此方法會將所指定的資料行`iColumn`排序資料行的清單。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CListCtrl 類別](../../mfc/reference/clistctrl-class.md)