---
title: 抽象 (C + + /cli 和 C + + /CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: d2cb8e6d1d60d4469e325a4380701beda49a4355
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645675"
---
# <a name="abstract--ccli-and-ccx"></a>抽象 (C + + /cli 和 C + + /CX)

**抽象**關鍵字會宣告其中一個：

- 類型可以當做基底類型，但是類型本身無法具現化。

- 類型成員函式只能在衍生的類型中定義。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>語法

*類別宣告**類別識別項***抽象 {}**

**虛擬***傳回型別**成員函式識別項* **（） 的抽象;**

### <a name="remarks"></a>備註

第一個範例語法會將類別宣告為抽象。 *類別宣告*元件可以是原生 c + + 宣告 (**類別**或是**結構**)，或 c + + 擴充功能宣告 (**ref 類別**或是**ref struct**) 如果`/ZW`或`/clr`指定編譯器選項。

第二個範例語法會將虛擬成員函式宣告為抽象。 將函式宣告為抽象等同於將它宣告為純虛擬函式。 將成員宣告為抽象也會造成含括類別被宣告為抽象。

**抽象**關鍵字支援原生與平台專屬的程式碼; 也就是說，它可以編譯包含或不含`/ZW`或`/clr`編譯器選項。

您可以在編譯時期偵測如果類型為抽象與`__is_abstract(type)`類型特性。 如需詳細資訊，請參閱 <<c0> [ 類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

**抽象**關鍵字是內容相關性的覆寫規範。 如需有關內容相關性關鍵字的詳細資訊，請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。 如需有關覆寫指定名稱的詳細資訊，請參閱[如何： 在原生編譯中宣告 「 覆寫規範](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

## <a name="windows-runtime"></a>Windows 執行階段

如需詳細資訊，請參閱 < [Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例會產生錯誤，因為類別`X`標示**抽象**。

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

下列程式碼範例會產生錯誤，因為它標示為原生類別會具現化**抽象**。 無論是否有 `/clr` 編譯器選項，都會發生此錯誤。

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

下列程式碼範例會產生錯誤，因為函式`f`包括定義，但會標示**抽象**。 在範例中的最後一個陳述式會顯示宣告抽象虛擬函式相當於宣告純虛擬函式。

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)
