---
title: mersenne_twister_engine 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::mersenne_twister_engine
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
ms.openlocfilehash: c0f30eacb308da61064a0383a6433b7127032a3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607450"
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine 類別

根據梅森旋轉演算法，產生高品質隨機整數序列。

## <a name="syntax"></a>語法

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>參數

*UIntType*<br/>
不帶正負號的整數結果類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。

*W*<br/>
**字組大小**。 狀態序列的每個字組大小 (位元)。 **前置條件**：`2u < W ≤ numeric_limits<UIntType>::digits`

*N*<br/>
**狀態大小**。 狀態序列中的元素數 (值)。

*M*<br/>
**移位大小**。 要在每個旋轉期間跳過的元素數。 **前置條件**：`0 < M ≤ N`

*R*<br/>
**遮罩位元**。 **前置條件**：`R ≤ W`

*A*<br/>
**XOR 遮罩**。 **前置條件**：`A ≤ (1u<<W) - 1u`

*U*， *S*， *T*， *L*<br/>
**調和移位參數**。 用做編碼 (調和) 期間的移位值。 前置條件：`U,S,T,L ≤ W`

*D*， *B*， *C*<br/>
**調和位元遮罩參數**。 用做編碼 (調和) 期間的位元遮罩值。 前置條件：`D,B,C ≤ (1u<<W) - 1u`

*F*<br/>
**初始化乘數**。 用於協助初始化序列。 前置條件：`F ≤ (1u<<W) - 1u`

## <a name="members"></a>Members

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` 是一個成員常數，定義為 `5489u`，用做 `mersenne_twister_engine::seed` 的預設參數值以及單一值建構函式。

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>備註

此範本類別描述亂數引擎，會傳回封閉間隔 [ `0`, `2`<sup>W</sup> - `1`] 的值。 它會保留具有 `W * (N - 1) + R` 位元的大整數值。 它會擷取*W*一次從這個大數值，並使用所有位元的位元它旋轉大數值移位和混合位元，使其具有一組新的位元為單位來擷取。 引擎的狀態是最後`N` `W`-位元值，如果使用`operator()`已至少呼叫*N*逾，否則`M` `W`-位元已使用的值，而最後`N - M`種子的值。

產生器反轉的大數值，它會使用移位值所定義的旋轉一般化的回饋移位暫存器保留*N*並*M*，旋轉值*R*，和條件式 XOR 遮罩*A*。此外，原始移位暫存的位元變碼 （調和） 值所定義的位元編碼矩陣*U*， *D*， *S*， *B*， *T*， *C*，和*L*。

範本引數 `UIntType` 必須大到足以保留多達 `2`<sup>W</sup> - `1` 的值。 其他範本引數的值必須滿足下列需求：`2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`。

雖然您可以直接從此引擎建構產生器，但是建議您使用下列其中一個預先定義的 typedef：

`mt19937`：32 位元梅森旋轉引擎 (Matsumoto 和 Nishimura，1998 年)。

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`：64 位元梅森旋轉引擎 (Matsumoto 和 Nishimura，2000 年)。

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

如需有關梅森旋轉演算法的詳細資訊，請參閱 Wikipedia 文章：[梅森旋轉算法](http://go.microsoft.com/fwlink/p/?linkid=402356)。

## <a name="example"></a>範例

如需程式碼範例，請參閱 [\<random>](../standard-library/random.md)。

## <a name="requirements"></a>需求

**標頭：**\<random>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)<br/>
