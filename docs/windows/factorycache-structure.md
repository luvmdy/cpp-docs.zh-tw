---
title: FactoryCache 結構
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 7196363567dffa43844bbbd1de76934a317302d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545843"
---
# <a name="factorycache-structure"></a>FactoryCache 結構

支援的 Windows 執行階段 c + + 樣板程式庫基礎結構，並不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>備註

包含的 class factory 和 wrt 識別已註冊的值或 COM 類別物件的位置。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

名稱                              | 描述
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[Factorycache:: Cookie](#cookie)   | 包含的值，識別已註冊的 Windows 執行階段或 COM 類別物件，並稍後用來取消註冊的物件。
[Factorycache:: Factory](#factory) | 指向 Windows 執行階段或 COM class factory。

## <a name="inheritance-hierarchy"></a>繼承階層

`FactoryCache`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL::Details

## <a name="cookie"></a>Factorycache:: Cookie

支援的 Windows 執行階段 c + + 樣板程式庫基礎結構，並不是直接從您的程式碼使用。

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>備註

包含的值，識別已註冊的 Windows 執行階段或 COM 類別物件，並稍後用來取消註冊的物件。

## <a name="factory"></a>Factorycache:: Factory

支援的 Windows 執行階段 c + + 樣板程式庫基礎結構，並不是直接從您的程式碼使用。

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>備註

指向 Windows 執行階段或 COM class factory。
