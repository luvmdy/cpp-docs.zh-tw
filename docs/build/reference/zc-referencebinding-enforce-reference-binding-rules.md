---
title: '/Zc: referencebinding （強制執行參考繫結規則）'
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: baf2106f015a4e8557cb8469d300709694e06d84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428323"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc: referencebinding （強制執行參考繫結規則）

當 **/zc: referencebinding**指定選項時，編譯器不允許非 const 左值參考繫結至暫存。

## <a name="syntax"></a>語法

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>備註

如果 **/zc: referencebinding**指定，則編譯器會遵循 C + + 11 標準 8.5.3 區段，而且不允許將暫存的使用者定義類型為非 const 左值參考繫結的運算式。 根據預設，或如果 **/Zc:referenceBinding-** 指定時，編譯器允許這類運算式做為 Microsoft 擴充功能，但不會發出層級 4 警告。 程式碼安全性、 可攜性和一致性，我們建議您使用 **/zc: referencebinding**。

**/Zc: referencebinding**選項預設為關閉。 [/Permissive--](permissive-standards-conformance.md)編譯器選項會隱含地設定此選項，但可以使用覆寫 **/Zc:referenceBinding-**。

## <a name="example"></a>範例

此範例會示範 Microsoft 擴充功能，可讓使用者定義型別的繫結到非 const 左值參考的暫存資料表。

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/zc: referencebinding** ，然後選擇**確定**。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
