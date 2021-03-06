---
title: /Ob (內嵌函式展開)
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: a53069c44e72d0d873ccb0b600c48480527d111f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582655"
---
# <a name="ob-inline-function-expansion"></a>/Ob (內嵌函式展開)

控制函式的內嵌展開。

## <a name="syntax"></a>語法

> /Ob {0 | 1 | 2}

## <a name="arguments"></a>引數

**0**<br/>
停用內嵌展開。 根據預設，展開，就會發生在由編譯器決定，所有的函式，通常稱為*自動內嵌*。

**1**<br/>
可展開的函式標示為僅[內嵌](../../cpp/inline-functions-cpp.md)， `__inline`，或`__forceinline`，或在類別宣告中所定義的 c + + 成員函式。

**2**<br/>
預設值。 可展開標記為 `inline`、`__inline` 或 `__forceinline` 的函式，以及編譯器所選擇的其他任何函式。

**/ Ob2**是何時生效[/o1，/o2 （最小大小、 最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或是[/Ox （啟用最速度最佳化）](../../build/reference/ox-full-optimization.md)用。

這個選項需要您啟用使用的最佳化 **/o1**， **/o2**， **/Ox**，或 **/Og**。

## <a name="remarks"></a>備註

編譯器會將內嵌展開選項和關鍵字視為建議， 而不會保證以內嵌方式展開所有函式。 您可以停用內嵌展開，但無法強制編譯器內嵌特定函式，即使是使用 `__forceinline` 關鍵字亦然。

您可以使用`#pragma` [auto_inline](../../preprocessor/auto-inline.md)指示詞，以從內嵌展開的候選考量中排除的函式。 另請參閱`#pragma`[內建](../../preprocessor/intrinsic.md)指示詞。

> [!NOTE]
> 從分析測試回合所收集的資訊會覆寫才會作用中您指定的最佳化 **/Ob**， **/Os**，或 **/Ot**。 如需詳細資訊，請參閱 <<c0> [ 特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 依序展開**組態屬性**， **C/c + +**，然後選取**最佳化**。

1. 修改**內嵌函式展開**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](../../build/reference/o-options-optimize-code.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)