---
title: ModuleBase 類別
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 4a65b7335626cc36a4eecbe61465778889a9e7e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502124"
---
# <a name="modulebase-class"></a>ModuleBase 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
class ModuleBase;
```

## <a name="remarks"></a>備註

表示基底類別[模組](../windows/module-class.md)類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                         | 描述
-------------------------------------------- | ---------------------------------------------------------
[Modulebase:: Modulebase](#modulebase)        | 初始化 `Module` 類別的執行個體。
[ModuleBase:: ~ ModuleBase](#tilde-modulebase) | 取消初始化目前的執行個體`Module`類別。

### <a name="public-methods"></a>公用方法

名稱                                                      | 描述
--------------------------------------------------------- | -------------------------------------------------------------------------
[Modulebase:: Decrementobjectcount](#decrementobjectcount) | 實作時，遞減模組所追蹤的物件數目。
[Modulebase:: Incrementobjectcount](#incrementobjectcount) | 實作時，遞增模組所追蹤的物件數目。

## <a name="inheritance-hierarchy"></a>繼承階層

`ModuleBase`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="tilde-modulebase"></a>ModuleBase:: ~ ModuleBase

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>備註

取消初始化目前的執行個體`ModuleBase`類別。

## <a name="decrementobjectcount"></a>Modulebase:: Decrementobjectcount

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>傳回值

遞減作業之前計數。

### <a name="remarks"></a>備註

實作時，遞減模組所追蹤的物件數目。

## <a name="incrementobjectcount"></a>Modulebase:: Incrementobjectcount

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>傳回值

之前的遞增作業計數。

### <a name="remarks"></a>備註

實作時，遞增模組所追蹤的物件數目。

## <a name="modulebase"></a>Modulebase:: Modulebase

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
ModuleBase();
```

### <a name="remarks"></a>備註

初始化 `Module` 類別的執行個體。
