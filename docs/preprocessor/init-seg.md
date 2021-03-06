---
title: init_seg
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: f11ec6d3cee7af2ce785555af9b73d8c0eb58638
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532612"
---
# <a name="initseg"></a>init_seg

**C + + 特定**

指定會影響啟始程式碼執行順序的關鍵字或程式碼區段。

## <a name="syntax"></a>語法

```
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )
```

## <a name="remarks"></a>備註

意義*區段*並*一節*是本主題中的可互換的。

由於全域靜態物件的初始化可能牽涉到執行程式碼，因此您必須指定關鍵字以定義何時建構物件。 若要使用特別重要**init_seg** pragma 在動態連結程式庫 (Dll) 或需要初始化的程式庫。

選項**init_seg** pragma 會：

*compiler*<br/>
針對 Microsoft C 執行階段程式庫初始化保留。 這個群組中的物件會最先結構。

*lib*<br/>
可供協力廠商類別程式庫廠商進行初始化。 此群組中的物件建構後標示*編譯器*但在任何其他項目之前。

*user*<br/>
可供任何使用者使用。 這個群組中的物件會最後結構。

*區段名稱*允許明確指定初始化區段。 在使用者指定的物件*區段名稱*不會隱含建構; 不過，將其位址放在名為區段*區段名稱*。

您提供的區段名稱將包含 Helper 函式的指標，這類函式將建構在該模組中 pragma 後面宣告的全域物件。

如需建立區段時，不應該使用的名稱，請參閱[/section](../build/reference/section-specify-section-attributes.md)。

*l o c k-n*指定的函式呼叫取代`atexit`程式結束時。 此協助程式函式也會呼叫[atexit](../c-runtime-library/reference/atexit.md)全域物件的解構函式的指標。 如果您使用下列形式的 pragma 指定函式識別項：

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

那麼將會呼叫您的函式，而不是 C 執行階段程式庫的 `atexit`。 這樣可讓您建立在您準備好終結物件時，需要呼叫的解構函式清單。

如果您需要延遲初始化 (例如在 DLL 中)，可以選擇明確指定區段名稱。 然後您必須呼叫每個靜態物件的建構函式。

取代 `atexit` 的識別項前後沒有引號。

您的物件仍將放在其他 XXX_seg pragma 所定義的區段中。

C 執行階段將不會自動初始化模組中宣告的物件。 您將需要自行進行這項作業。

根據預設，`init_seg` 區段是唯讀的。 如果區段名稱是 .CRT，即使屬性標記為讀取、寫入，編譯器仍會以無訊息方式將屬性變更為唯讀。

您無法指定**init_seg**不止一次在轉譯單位中。

即使您的物件沒有使用者定義的建構函式 (未在程式碼中明確定義的建構函式)，編譯器仍可能會產生這類建構函式 (例如，用於繫結 v-table 指標)。 因此，您的程式碼必須呼叫編譯器產生的建構函式。

## <a name="example"></a>範例

```cpp
// pragma_directive_init_seg.cpp
#include <stdio.h>
#pragma warning(disable : 4075)

typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors we need to call
PF pfx[200];    // pointers to destructors.

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() { puts("A()"); }
   ~A() { puts("~A()"); }
};

// ctor & dtor called by CRT startup code
// because this is before the pragma init_seg
A aaaa;

// The order here is important.
// Section names must be 8 characters or less.
// The sections with the same name before the $
// are merged into one section. The order that
// they are merged is determined by sorting
// the characters after the $.
// InitSegStart and InitSegEnd are used to set
// boundaries so we can find the real functions
// that we need to call for initialization.

#pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;

#pragma section(".mine$z",read)
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;

// The comparison for 0 is important.
// For now, each section is 256 bytes. When they
// are merged, they are padded with zeros. You
// can't depend on the section being 256 bytes, but
// you can depend on it being padded with zeros.

void InitializeObjects () {
   const PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x) (*x)();
}

void DestroyObjects () {
   while (cxpf>0) {
      --cxpf;
      (pfx[cxpf])();
   }
}

// by default, goes into a read only section
#pragma init_seg(".mine$m", myexit)

A bbbb;
A cccc;

int main () {
   InitializeObjects();
   DestroyObjects();
}
```

```Output
A()
A()
A()
~A()
~A()
~A()
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)