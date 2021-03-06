---
title: '&lt;exception&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: e599a725feb46eaa90023fdb9c999f5b2d159637
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522035"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

定義數個與例外狀況處理有關的類型和函式。 在系統可從錯誤復原的情況下，使用例外狀況處理。 它提供方式，將控制從函式傳回至程式。 併入例外狀況處理的目標是增加程式穩定性，同時以有次序的方式從錯誤復原。

## <a name="syntax"></a>語法

```cpp
#include <exception>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|描述例外狀況指標的類型。|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|類型，描述適合做為 `terminate_handler` 之函式的指標。|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|類型，描述適合做為 `unexpected_handler` 之函式的指標。|

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|取得目前例外狀況的指標。|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|取得目前的 `terminate_handler` 函式。|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|取得目前的 `unexpected_handler` 函式。|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|建立持有例外狀況複本的 `exception_ptr` 物件。|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|擲回做為參數傳遞的例外狀況。|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|建立新 `terminate_handler`，在程式終止時呼叫。|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|建立新的 `unexpected_handler`，當未預期的例外狀況發生時擲回。|
|[terminate](../standard-library/exception-functions.md#terminate)|呼叫終止處理常式。|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|只有當系統正在處理擲回的例外狀況時，才傳回 **true**。|
|[unexpected](../standard-library/exception-functions.md#unexpected)|呼叫未預期的處理常式。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[bad_exception 類別](../standard-library/bad-exception-class.md)|此類別描述從 `unexpected_handler` 所擲回的例外狀況。|
|[exception 類別](../standard-library/exception-class.md)|此類別可作為特定運算式和 C++ 標準程式庫所擲回之所有例外狀況的基底類別。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
