---
title: freelist 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: ef1f2e617e93869a1084dc030c6496c819f1ed96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652708"
---
# <a name="freelist-class"></a>freelist 類別

可管理記憶體區塊的清單。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*sz*|所配置陣列中的元素數。|
|*最大值*|max 類別，表示可在可用清單中儲存的元素數量上限。 max 類別可以是 [max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_fixed_size](../standard-library/max-fixed-size-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>備註

此範本類別會管理記憶體區塊大小的清單*Sz*傳入的 max 類別所決定之清單的最大長度*Max*。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[freelist](#freelist)|建構類型 `freelist` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[pop](#pop)|從可用清單中移除第一個記憶體區塊。|
|[push](#push)|將記憶體區塊新增至清單中。|

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="freelist"></a>  freelist::freelist

建構類型 `freelist` 的物件。

```cpp
freelist();
```

### <a name="remarks"></a>備註

## <a name="pop"></a>  freelist::pop

從可用清單中移除第一個記憶體區塊。

```cpp
void *pop();
```

### <a name="return-value"></a>傳回值

傳回從清單中移除之記憶體區塊的指標。

### <a name="remarks"></a>備註

如果清單是空的此成員函式會傳回 NULL。 否則，會從清單中移除第一個記憶體區塊。

## <a name="push"></a>  freelist::push

將記憶體區塊新增至清單中。

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|要新增至可用清單的記憶體區塊指標。|

### <a name="return-value"></a>傳回值

**true**如果`full`max 類別的函式會傳回**false**，否則`push`函式會傳回**false**。

### <a name="remarks"></a>備註

如果`full`max 類別的函式會傳回**假**，此成員函式會將指向的記憶體區塊*ptr*標頭的清單。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
