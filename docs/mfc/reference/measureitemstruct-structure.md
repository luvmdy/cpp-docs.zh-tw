---
title: MEASUREITEMSTRUCT 結構
ms.date: 11/04/2016
f1_keywords:
- MEASUREITEMSTRUCT
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
ms.openlocfilehash: 3f541c30c484041d855807f220345d6863a780d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575033"
---
# <a name="measureitemstruct-structure"></a>MEASUREITEMSTRUCT 結構

`MEASUREITEMSTRUCT`結構會通知 Windows 的主控描繪控制項或功能表項目的維度。

## <a name="syntax"></a>語法

```
typedef struct tagMEASUREITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    UINT itemWidth;
    UINT itemHeight;
    DWORD itemData
} MEASUREITEMSTRUCT;
```

#### <a name="parameters"></a>參數

*CtlType*<br/>
包含的控制項型別。 控制項類型的值如下：

- ODT_COMBOBOX 主控描繪下拉式方塊

- ODT_LISTBOX 主控描繪清單方塊

- ODT_MENU 主控描繪功能表

*CtlID*<br/>
包含下拉式方塊、 清單方塊或按鈕的控制項識別碼。 這個成員無法用於功能表。

*項目識別碼*<br/>
包含功能表的功能表項目識別碼或變動高度下拉式方塊或清單方塊的清單方塊項目識別碼。 固定高度下拉式方塊或清單方塊或按鈕時，不會使用這個成員。

*itemWidth*<br/>
指定功能表項目的寬度。 主控描繪功能表項目的擁有者必須填妥此成員，它會傳回訊息之前。

*itemHeight*<br/>
指定清單方塊或功能表中的個別項目的高度。 它會傳回訊息的主控描繪下拉式方塊中，擁有者才能清單方塊或功能表項目必須填寫此成員。 清單方塊項目的的最大高度為 255。

*itemData*<br/>
對於下拉式方塊或清單方塊，這個成員會包含已由下列其中一項傳遞至清單方塊的值：

- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)

- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)

- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)

- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)

對於功能表，這個成員會包含已由下列其中一項傳遞至功能表的值：

- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)

- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)

- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)

這可讓 Windows 才能正確處理使用者與控制項互動。 若未填妥中的適當成員`MEASUREITEMSTRUCT`結構會導致控制項的作業不正確。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

