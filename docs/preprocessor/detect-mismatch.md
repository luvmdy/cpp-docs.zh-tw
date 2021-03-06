---
title: detect_mismatch
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: 2973a4738aa54e9f454190b18bcabff92077b284
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633320"
---
# <a name="detectmismatch"></a>detect_mismatch
在物件中放入記錄。 連結器會檢查這些記錄是否有不相符之處。

## <a name="syntax"></a>語法

```
#pragma detect_mismatch( "name", "value"))
```

## <a name="remarks"></a>備註

當您連結專案時，如果專案包含兩個具有同一個 `LNK2038` 的物件，但其中一個物件的 `name` 不同，則連結器會擲回 `value` 錯誤。 使用這個 pragma 可防止連結不一致的目的檔。

名稱和數值都是字串常值，而且遵守字串常值的逸出字元與串連規則。 它們會區分大小寫，而且不能包含逗號、 等號、 引號或**null**字元。

## <a name="example"></a>範例

這個範例會建立兩個版本號碼不同但版本標籤相同的檔案。

```cpp
// pragma_directive_detect_mismatch_a.cpp
#pragma detect_mismatch("myLib_version", "9")
int main ()
{
   return 0;
}

// pragma_directive_detect_mismatch_b.cpp
#pragma detect_mismatch("myLib_version", "1")
```

如果您使用命令列 `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` 編譯這兩個檔案，將會收到 `LNK2038` 錯誤。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)