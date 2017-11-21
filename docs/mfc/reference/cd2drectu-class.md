---
title: "CD2DRectU 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 50347c96bf4e2d75be0528bcc5860d1677e6c6f7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="cd2drectu-class"></a>CD2DRectU 類別
`D2D1_RECT_U`的包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DRectU : public D2D1_RECT_U;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DRectU::CD2DRectU](#cd2drectu)|多載。 建構`CD2DRectU`物件從`D2D1_RECT_U`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DRectU::IsNull](#isnull)|傳回`boolean`值，指出運算式是否包含任何有效的資料 ( `null`)。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DRectU::operator CRect](#operator_crect)|將轉換`CD2DRectU`至`CRect`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `D2D1_RECT_U`  
  
 `CD2DRectU`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="cd2drectu"></a>CD2DRectU::CD2DRectU  
 建構來自 CRect 物件 CD2DRectU 物件。  
  
```  
CD2DRectU(const CRect& rect);  
CD2DRectU(const D2D1_RECT_U& rect);  
  CD2DRectU(const D2D1_RECT_U* rect);

 
CD2DRectU(
    UINT32 uLeft = 0,  
    UINT32 uTop = 0,  
    UINT32 uRight = 0,  
    UINT32 uBottom = 0);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 來源矩形  
  
 `uLeft`  
 來源左方的座標  
  
 `uTop`  
 來源的上方座標  
  
 `uRight`  
 來源右方座標  
  
 `uBottom`  
 來源下方座標  
  
##  <a name="isnull"></a>CD2DRectU::IsNull  
 傳回布林值，指出運算式是否包含任何有效的資料 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>傳回值  
 矩形的頂端、 左邊、 下框線和右值所有等於 0; 如果為 TRUE否則為 FALSE。  
  
##  <a name="operator_crect"></a>CD2DRectU::operator CRect  
 將 CD2DRectU 轉換 CRect 物件。  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>傳回值  
 D2D 矩形的目前值。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
