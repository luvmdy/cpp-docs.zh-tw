---
title: WM_ 訊息處理常式：L - M
ms.date: 11/04/2016
f1_keywords:
- ON_WM_MENUSELECT
- ON_WM_MBUTTONDBLCLK
- ON_WM_MOUSEACTIVATE
- ON_WM_MOUSEMOVE
- ON_WM_MOVING
- ON_WM_LBUTTONUP
- ON_WM_LBUTTONDBLCLK
- ON_WM_MEASUREITEM
- ON_WM_MDIACTIVATE
- ON_WM_MOVE
- ON_WM_LBUTTONDOWN
- ON_WM_MBUTTONDOWN
- ON_WM_MENUCHAR
- ON_WM_MBUTTONUP
helpviewer_keywords:
- ON_WM_MENUSELECT [MFC]
- ON_WM_MBUTTONDBLCLK [MFC]
- ON_WM_MOVE [MFC]
- ON_WM_MOUSEACTIVATE [MFC]
- ON_WM_MBUTTONUP [MFC]
- ON_WM_MOUSEMOVE [MFC]
- ON_WM_MENUCHAR [MFC]
- ON_WM_MBUTTONDOWN [MFC]
- ON_WM_MEASUREITEM [MFC]
- ON_WM_MOVING [MFC]
- ON_WM_LBUTTONDOWN [MFC]
- ON_WM_MDIACTIVATE [MFC]
- ON_WM_LBUTTONDBLCLK [MFC]
- ON_WM_LBUTTONUP [MFC]
- WM_ messages
ms.assetid: 96ecaaf1-6d13-4e12-a454-535635967489
ms.openlocfilehash: 395bd7f627fe85b8bb763bdb1e75ae36c91b3061
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550458"
---
# <a name="wm-message-handlers-l---m"></a>WM_ 訊息處理常式：L - M

左邊的下列對應項目對應於右邊的函式原型：

|對應項目|函式原型|
|---------------|------------------------|
|ON_WM_LBUTTONDBLCLK()|afx_msg void [OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)UINT (CPoint）;|
|ON_WM_LBUTTONDOWN()|afx_msg void [OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)UINT (CPoint）;|
|ON_WM_LBUTTONUP()|afx_msg void [OnLButtonUp](../../mfc/reference/cwnd-class.md#onlbuttonup)UINT (CPoint）;|
|ON_WM_MBUTTONDBLCLK()|afx_msg void [OnMButtonDblClk](../../mfc/reference/cwnd-class.md#onmbuttondblclk)UINT (CPoint）;|
|ON_WM_MBUTTONDOWN()|afx_msg void [OnMButtonDown](../../mfc/reference/cwnd-class.md#onmbuttondown)UINT (CPoint）;|
|ON_WM_MBUTTONUP()|afx_msg void [OnMButtonUp](../../mfc/reference/cwnd-class.md#onmbuttonup)UINT (CPoint）;|
|ON_WM_MDIACTIVATE()|afx_msg void [OnMDIActivate](../../mfc/reference/cwnd-class.md#onmdiactivate)(BOOL，CWnd\*，CWnd\*);|
|ON_WM_MEASUREITEM()|afx_msg void [OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)(LPMEASUREITEMSTRUCT);|
|ON_WM_MENUCHAR()|afx_msg 長期[OnMenuChar](../../mfc/reference/cwnd-class.md#onmenuchar)(UINT，UINT，CMenu\*);|
|ON_WM_MENUDRAG()|afx_msg UINT [OnMenuDrag](../../mfc/reference/cwnd-class.md#onmenudrag)(UINT，CMenu\*);|
|ON_WM_MENUGETOBJECT()|afx_msg UINT [OnMenuGetObject](../../mfc/reference/cwnd-class.md#onmenugetobject)(MENUGETOBJECTINFO\*);|
|ON_WM_MENURBUTTONUP()|afx_msg void [OnMenuRButtonUp](../../mfc/reference/cwnd-class.md#onmenurbuttonup)(UINT，CMenu\*);|
|ON_WM_MENUSELECT()|afx_msg void [OnMenuSelect](../../mfc/reference/cwnd-class.md#onmenuselect)（UINT，UINT，HMENU）;|
|ON_WM_MOUSEACTIVATE()|afx_msg int [OnMouseActivate](../../mfc/reference/cwnd-class.md#onmouseactivate)(CWnd\*，UINT，UINT);|
|ON_WM_MOUSEHOVER()|afx_msg void [OnMouseHover](../../mfc/reference/cwnd-class.md#onmousehover)UINT (CPoint）;|
|ON_WM_MOUSEHWHEEL()|afx_msg void [OnMouseHWheel](../../mfc/reference/cwnd-class.md#onmousehwheel)(UINT、 short、 CPoint);|
|ON_WM_MOUSELEAVE()|afx_msg void[了 OnMouseLeave](../../mfc/reference/cwnd-class.md#onmouseleave)（);|
|ON_WM_MOUSEMOVE()|afx_msg void [OnMouseMove](../../mfc/reference/cwnd-class.md#onmousemove)UINT (CPoint）;|
|ON_WM_MOUSEWHEEL()|afx_msg BOOL [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)(UINT、 short、 CPoint);|
|ON_WM_MOVE()|afx_msg void [OnMove](../../mfc/reference/cwnd-class.md#onmove)(int，int;)|
|ON_WM_MOVING()|afx_msg void [OnMoving](../../mfc/reference/cwnd-class.md#onmoving)UINT (LPRECT）;|

## <a name="see-also"></a>另請參閱

[訊息對應](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 訊息的處理常式](../../mfc/reference/handlers-for-wm-messages.md)

