---
title: 例外狀況處理巨集
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: cf4b7ffb8c6b197dc1c4eea4b6c569e173bb188d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544400"
---
# <a name="exception-handling-macros"></a>例外狀況處理巨集

這些巨集提供例外狀況處理支援。

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|陳述式來處理發生在相關聯的錯誤`_ATLTRY`。|
|[_ATLCATCHALL](#_atlcatchall)|陳述式來處理發生在相關聯的錯誤`_ATLTRY`。|
|[_ATLTRY](#_atltry)|標記可能發生的錯誤可能受防護的程式碼區段。|

## <a name="requirements"></a>需求：

**標頭：** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

陳述式來處理發生在相關聯的錯誤`_ATLTRY`。

```
_ATLCATCH(e)
```

### <a name="parameters"></a>參數

*e*<br/>
若要攔截例外狀況。

### <a name="remarks"></a>備註

用於搭配`_ATLTRY`。 會解析成 c + +[攔截 (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md)處理針對給定的 c + + 例外狀況類型。

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

陳述式來處理發生在相關聯的錯誤`_ATLTRY`。

```
_ATLCATCHALL
```

### <a name="remarks"></a>備註

用於搭配`_ATLTRY`。 會解析成 c + + [catch](../../cpp/try-throw-and-catch-statements-cpp.md)來處理所有類型的 c + + 例外狀況。

##  <a name="_atltry"></a>  _ATLTRY

標記可能發生的錯誤可能受防護的程式碼區段。

```
_ATLTRY
```

### <a name="remarks"></a>備註

用於搭配[_ATLCATCH](#_atlcatch)或是[_ATLCATCHALL](#_atlcatchall)。 C + + 符號會解析[嘗試](../../cpp/try-throw-and-catch-statements-cpp.md)。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
