---
title: independent_bits_engine 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 8f420ca054d20cd222b8eda9a4a35a383a8e535a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635834"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine 類別

重新封裝基底引擎所傳回值的位元，以產生具有指定位元數的隨機一連串數字。

## <a name="syntax"></a>語法

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>參數

*引擎*<br/>
基底引擎類型。

*W*<br/>
**字組大小**。 每個所產生數字的大小 (位元)。 **前置條件**：`0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*<br/>
不帶正負號的整數結果類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。

## <a name="members"></a>成員

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>備註

此範本類別描述*引擎配接器*產生的值導致其基底引擎所傳回的值的位元重新封裝*W*-位元值。

## <a name="requirements"></a>需求

**標頭：**\<random>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)<br/>
