---
title: CMFCPropertyPage 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: a55a1a8cd5d63a9e775038824a7bbbe91adbae01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566734"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 類別

`CMFCPropertyPage`類別支援的快顯功能表顯示在 [屬性] 頁面上。

## <a name="syntax"></a>語法

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|建構 `CMFCPropertyPage` 物件。|
|`CMFCPropertyPage::~CMFCPropertyPage`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCPropertyPage::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|`CMFCPropertyPage::OnSetActive`|此成員函式是由架構呼叫，當頁面由使用者選擇而變成使用中的頁面。 (覆寫[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。)|
|`CMFCPropertyPage::PreTranslateMessage`|將轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 如需詳細資訊及方法語法，請參閱 < [cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CPropertyPage::PreTranslateMessage`。)|

## <a name="remarks"></a>備註

`CMFCPropertyPage`類別表示屬性工作表，亦稱為索引標籤對話方塊中的個別頁面。

使用`CMFCPropertyPage`類別搭配[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)類別。 若要使用的屬性頁功能表，取代所有出現之`CPropertyPage`類別搭配`CMFCPropertyPage`類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertypage.h

##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage

建構 `CMFCPropertyPage` 物件。

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>參數

*nIDTemplate*<br/>
此頁面的範本的資源識別碼。

*nIDCaption*<br/>
資源識別碼的標籤將放在這個頁面的索引標籤。 如果為 0，名稱被取自此頁面的對話方塊範本中。 預設值為 0。

*lpszTemplateName*<br/>
此頁面的範本名稱點。 不可以是 NULL。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

如需有關建構函式參數的詳細資訊，請參閱[CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)
