---
title: _com_ptr_t 擷取器
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: bac1f9a139d2fb0092ef0869587ae8b54342fe82
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330316"
---
# <a name="comptrt-extractors"></a>_com_ptr_t 擷取器

**Microsoft 專屬**

擷取封裝的 COM 介面指標。

## <a name="syntax"></a>語法

```
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>備註

- **運算子 Interface&** <strong>\*</strong>傳回封裝的介面指標，可能是 NULL。

- **運算子 Interface& &** 傳回封裝的介面指標的參考，並發出錯誤，如果指標為 NULL。

- **運算子**<strong>\*</strong>可讓智慧型指標物件，如同它已實際封裝的介面取值時採取行動。

- **operator->** 可讓智慧型指標物件，如同它已實際封裝的介面取值時採取行動。

- **運算子 &** 釋放任何封裝的介面指標，它取代為 NULL，並傳回封裝的指標位址。 這可讓智慧型指標的位址傳遞至函式*出*透過它傳回介面指標的參數。

- **運算子 bool**讓智慧型指標物件可用於條件運算式。 如果指標不是 NULL，這個運算子會傳回 TRUE。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)