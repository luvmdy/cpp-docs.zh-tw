---
title: regex_token_iterator 類別
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 2cb66ce4cbee0936211e5e991b18f3ae4b8a7fe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473511"
---
# <a name="regextokeniterator-class"></a>regex_token_iterator 類別

子相符項目的迭代器類別。

## <a name="syntax"></a>語法

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>參數

*BidIt*<br/>
子相符項目的迭代器類型。

*Elem*<br/>
要符合之項目的類型。

*RXtraits*<br/>
項目的 Traits 類別。

## <a name="remarks"></a>備註

此樣板類別描述常數正向迭代器物件。 就概念而言，它會保存 `regex_iterator` 物件，以用來搜尋字元序列中的規則運算式相符項目。 它會擷取 `sub_match<BidIt>` 類型的物件，該物件代表針對每個規則運算式相符項目儲存的向量 `subs` 中的索引值所識別的子相符項目。

索引值 -1 指定字元序列會在上一個規則運算式相符項目的結尾之後立即開始，如果之前沒有任何規則運算式相符項目，則會從字元序列的開頭開始，並延伸到 (但不包含) 目前規則運算式相符項目的第一個字元，如果目前沒有相符項目，則延伸到字元序列的結尾。 其他任何索引值 `idx` 則指定 `it.match[idx]`中所保留之擷取群組的內容。

### <a name="members"></a>成員

|成員|預設值|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|建構迭代器。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[difference_type](#difference_type)|迭代器差值的類型。|
|[iterator_category](#iterator_category)|迭代器分類的類型。|
|[pointer](#pointer)|要比對的指標類型。|
|[reference](#reference)|子對應的參考類型。|
|[regex_type](#regex_type)|要比對的規則運算式類型。|
|[value_type](#value_type)|子對應的類型。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|比較迭代器是否不相等。|
|[operator*](#op_star)|存取指定的子對應項目。|
|[operator++](#op_add_add)|遞增迭代器。|
|[operator==](#op_eq_eq)|比較迭代器是否相等。|
|[operator->](#op_arrow)|存取指定的子對應項目。|

## <a name="requirements"></a>需求

**標頭︰**\<regex>

**命名空間：** std

## <a name="example"></a>範例

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="difference_type"></a>  regex_token_iterator::difference_type

迭代器差值的類型。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>備註

此類型是 `std::ptrdiff_t` 的同義字。

## <a name="iterator_category"></a>  regex_token_iterator::iterator_category

迭代器分類的類型。

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>備註

此類型是 `std::forward_iterator_tag` 的同義字。

## <a name="op_neq"></a>  regex_token_iterator::operator!=

比較迭代器是否不相等。

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>參數

*right*<br/>
要比較的迭代器。

### <a name="remarks"></a>備註

成員函式會傳回 `!(*this == right)`。

## <a name="op_star"></a>  regex_token_iterator::operator*

存取指定的子對應項目。

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>備註

成員函式會傳回 `sub_match<BidIt>` 物件，以代表索引值 `subs[pos]`所識別之擷取群組。

## <a name="op_add_add"></a>  regex_token_iterator::operator++

遞增迭代器。

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>備註

如果預存迭代器 `it` 是序列結尾迭代器，則第一個運算子會將預存值 `pos` 設為 `subs.size()` 的值 (因而產生序列結尾迭代器)。 否則，運算子遞增預存值 `pos`；如果結果等於值 `subs.size()`，它會將預存值 `pos` 設為零，並遞增預存迭代器 `it`。 如果預存迭代器在遞增後變得不等於序列結尾迭代器，則運算子不會有進一步動作。 否則，如果先前比對的結尾就是字元序列的結尾，則運算子會將 `pos` 的預存值設為 `subs.size()`。 否則，運算子會重複遞增預存值 `pos`，直到 `pos == subs.size()` 或 `subs[pos] == -1` 為止 (以確保在其中一個索引值為 -1 時，迭代器的下一個取值會傳回字元序列的結尾)。 在所有情況下，運算子都會傳回物件。

第二個運算子會複製物件、遞增物件，然後傳回複本。

## <a name="op_eq_eq"></a>  regex_token_iterator::operator==

比較迭代器是否相等。

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>參數

*right*<br/>
要比較的迭代器。

### <a name="remarks"></a>備註

成員函式會傳回 `it == right.it && subs == right.subs && pos == right.pos`。

## <a name="op_arrow"></a>  regex_token_iterator::operator-&gt;

存取指定的子對應項目。

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>備註

成員函式會傳回 `sub_match<BidIt>` 物件的指標，以代表索引值 `subs[pos]`所識別之擷取群組。

## <a name="pointer"></a>  regex_token_iterator::pointer

要比對的指標類型。

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>備註

此類型與 `sub_match<BidIt>*`同義，其中 `BidIt` 是範本參數。

## <a name="reference"></a>  regex_token_iterator::reference

子對應的參考類型。

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>備註

此類型與 `sub_match<BidIt>&`同義，其中 `BidIt` 是範本參數。

## <a name="regex_token_iterator"></a>  regex_token_iterator::regex_token_iterator

建構迭代器。

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>參數

*first*<br/>
要比對的序列開頭。

*最後一個*<br/>
要比對的序列結尾。

*re*<br/>
比對的規則運算式。

*f*<br/>
比對的旗標。

### <a name="remarks"></a>備註

第一個建構函式會建構結束序列 (end-of-sequence) 迭代器。

第二個建構函式會建構一個物件，其儲存的迭代器 `it` 已初始化為 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`、其儲存的向量 `subs` 只會保留一個整數值 `submatch`，而其儲存值 `pos` 則為零。 注意：產生的物件會在每次規則運算式比對成功時，擷取索引值 `submatch` 所識別的子相符項目。

第三個建構函式會建構一個物件，其儲存的迭代器 `it` 已初始化為 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`、其儲存的向量 `subs` 會保留建構函式引數 `submatches`的一個複本，而其儲存值 `pos` 則為零。

第四個建構函式會建構一個物件，其儲存的迭代器 `it` 已初始化為 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`、其儲存的向量 `subs` 會保留建構函式引數 `N` 所指向的 `submatches`值，而其儲存值 `pos` 則為零。

## <a name="regex_type"></a>  regex_token_iterator::regex_type

要比對的規則運算式類型。

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>備註

此 typedef 是 `basic_regex<Elem, RXtraits>`的同義字。

## <a name="value_type"></a>  regex_token_iterator::value_type

子對應的類型。

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>備註

此類型與 `sub_match<BidIt>`同義，其中 `BidIt` 是範本參數。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 類別](../standard-library/regex-constants-class.md)<br/>
[regex_error 類別](../standard-library/regex-error-class.md)<br/>
[\<regex> 函式](../standard-library/regex-functions.md)<br/>
[regex_iterator 類別](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 運算子](../standard-library/regex-operators.md)<br/>
[regex_traits 類別](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
