---
title: CAutoPtrArray 類別
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: c7a2a7e9592b120204582334f69e27e72cd7364f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677938"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray 類別

建構的智慧型指標陣列時，這個類別會提供有用的方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>參數

*E*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|建構函式。|

## <a name="remarks"></a>備註

這個類別提供建構函式，並衍生方法從[CAtlArray](../../atl/reference/catlarray-class.md)並[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)協助儲存智慧型指標的集合類別物件的建立。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray

建構函式。

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>備註

初始化智慧型指標陣列。

## <a name="see-also"></a>另請參閱

[CAtlArray 類別](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits 類別](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList 類別](../../atl/reference/cautoptrlist-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
