---
title: error_code 類別
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
ms.openlocfilehash: f4d0bc2c2922374d27bba3c0693e50f7930dbe67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593280"
---
# <a name="errorcode-class"></a>error_code 類別

表示實作特定的低層級系統錯誤。

## <a name="syntax"></a>語法

```cpp
class error_code;
```

## <a name="remarks"></a>備註

類型為 `error_code` 類別的物件會儲存錯誤碼值和物件指標，該物件表示的錯誤碼[分類](../standard-library/error-category-class.md)可描述回報的低層級系統錯誤。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[error_code](#error_code)|建構類型 `error_code` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[value_type](#value_type)|此類型表示預存的錯誤碼值。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[assign](#assign)|可針對錯誤碼指派錯誤碼值和分類。|
|[category](#category)|傳回錯誤分類。|
|[clear](#clear)|清除錯誤碼值和分類。|
|[default_error_condition](#default_error_condition)|傳回預設的錯誤狀況。|
|[message](#message)|傳回錯誤碼的名稱。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator==](#op_eq_eq)|測試 `error_code` 物件是否相等。|
|[operator!=](#op_neq)|測試 `error_code` 物件是否不相等。|
|[operator<](#op_lt)|測試 `error_code` 物件是否小於傳入以進行比較的 `error_code` 物件。|
|[operator=](#op_eq)|將新的列舉值指派給 `error_code` 物件。|
|[operator bool](#op_bool)|轉換 `error_code` 類型的變數。|

## <a name="requirements"></a>需求

**標頭：**\<system_error>

**命名空間：** std

## <a name="assign"></a>  error_code::assign

可針對錯誤碼指派錯誤碼值和分類。

```cpp
void assign(value_type val, const error_category& _Cat);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*val*|要儲存在 `error_code` 中的錯誤碼值。|
|*與*|要儲存在 `error_code` 中的錯誤分類。|

### <a name="remarks"></a>備註

此成員函式會*val*作為錯誤碼值和指標*與*。

## <a name="category"></a>  error_code::category

傳回錯誤分類。

```cpp
const error_category& category() const;
```

### <a name="remarks"></a>備註

## <a name="clear"></a>  error_code::clear

清除錯誤碼值和分類。

```cpp
clear();
```

### <a name="remarks"></a>備註

成員函式會儲存零的錯誤碼值以及 [generic_category](../standard-library/system-error-functions.md#generic_category) 物件的指標。

## <a name="default_error_condition"></a>  error_code::default_error_condition

傳回預設的錯誤狀況。

```cpp
error_condition default_error_condition() const;
```

### <a name="return-value"></a>傳回值

[default_error_condition](../standard-library/error-category-class.md#default_error_condition) 所指定的 [error_condition](../standard-library/error-condition-class.md)。

### <a name="remarks"></a>備註

此成員函式會傳回 `category().default_error_condition(value())`。

## <a name="error_code"></a>  error_code::error_code

建構類型 `error_code` 的物件。

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*val*|要儲存在 `error_code` 中的錯誤碼值。|
|*與*|要儲存在 `error_code` 中的錯誤分類。|
|*_Errcode*|要儲存在 `error_code` 中的列舉值。|

### <a name="remarks"></a>備註

第一個建構函式會儲存零的錯誤碼值以及 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指標。

第二個建構函式儲存*val*作為錯誤碼值和指標[error_category](../standard-library/error-category-class.md)。

第三個建構函式會儲存 `(value_type)_Errcode` 作為錯誤碼值，並儲存 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指標。

## <a name="message"></a>  error_code::message

傳回錯誤碼的名稱。

```cpp
string message() const;
```

### <a name="return-value"></a>傳回值

`string`，表示錯誤碼的名稱。

### <a name="remarks"></a>備註

此成員函式會傳回 `category().message(value())`。

## <a name="op_eq_eq"></a>  error_code::operator==

測試 `error_code` 物件是否相等。

```cpp
bool operator==(const error_code& right) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*right*|要測試是否相等的物件。|

### <a name="return-value"></a>傳回值

如果物件相等，即為 **true**；如果物件不相等，則為 **false**。

### <a name="remarks"></a>備註

此成員運算子會傳回 `category() == right.category() && value == right.value()`。

## <a name="op_neq"></a>  error_code::operator!=

測試 `error_code` 物件是否不相等。

```cpp
bool operator!=(const error_code& right) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*right*|要測試是否不相等的物件。|

### <a name="return-value"></a>傳回值

**true**如果`error_code`物件是否不等於`error_code`傳入物件*右*; 否則為**false**。

### <a name="remarks"></a>備註

此成員運算子會傳回 `!(*this == right)`。

## <a name="op_lt"></a>  error_code::operator&lt;

測試 `error_code` 物件是否小於傳入以進行比較的 `error_code` 物件。

```cpp
bool operator<(const error_code& right) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*right*|要比較的 error_code 物件。|

### <a name="return-value"></a>傳回值

如果 `error_code` 小於傳入以進行比較的 `error_code` 物件，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

此成員運算子會傳回 `category() < right.category() || category() == right.category() && value < right.value()`。

## <a name="op_eq"></a>  error_code::operator=

將新的列舉值指派給 `error_code` 物件。

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Errcode*|要指派給 `error_code` 物件的列舉值。|

### <a name="return-value"></a>傳回值

`error_code` 物件的參考，該物件為成員函式要指派新列舉值的目標 。

### <a name="remarks"></a>備註

成員運算子會儲存 `(value_type)_Errcode` 作為錯誤碼值，並儲存 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指標。 它會傳回 `*this`。

## <a name="op_bool"></a>  error_code::operator bool

轉換 `error_code` 類型的變數。

```cpp
explicit operator bool() const;
```

### <a name="return-value"></a>傳回值

`error_code` 物件的布林值。

### <a name="remarks"></a>備註

此運算子會傳回值轉換為 **，則為 true**只有當[值](#value)不等於零。 傳回的型別會轉換才能**bool**，而非`void *`或其他已知的純量類型。

## <a name="value"></a>  error_code::value

傳回預存的錯誤碼值。

```cpp
value_type value() const;
```

### <a name="return-value"></a>傳回值

[value_type](#value_type) 類型的預存錯誤碼值。

### <a name="remarks"></a>備註

## <a name="value_type"></a>  error_code::value_type

此類型表示預存的錯誤碼值。

```cpp
typedef int value_type;
```

### <a name="remarks"></a>備註

此類型定義是同義**int**。

## <a name="see-also"></a>另請參閱

[error_category 類別](../standard-library/error-category-class.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
