---
title: /Z7、/Zi、/ZI (偵錯資訊格式)
ms.date: 02/22/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: 43ffbe76092b9675be1610e58c65c0034955634f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479036"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI (偵錯資訊格式)

指定為您的程式，以及這項資訊保留在物件檔，還是在程式資料庫 (PDB) 檔案中建立的偵錯資訊類型。

## <a name="syntax"></a>語法

> **/Z**{**7**|**i**|**I**}

## <a name="remarks"></a>備註

當編譯程式碼，並內建的偵錯模式下時，編譯器會產生函式和變數、 型別資訊和列數字的位置以供偵錯工具的符號名稱。 這個符號的偵錯資訊可以包含在由編譯器產生目的檔 （.obj 檔案），或在不同的 PDB 檔案 （.pdb 檔案） 可執行檔。  偵錯資訊格式選項是由下列各節所述。

### <a name="none"></a>無

根據預設，如果偵錯資訊格式未不指定任何選項，編譯器會產生任何偵錯的資訊，讓編譯快一些。

### <a name="z7"></a>/Z7

**/Z7**選項會產生目的檔也包含完整符號偵錯資訊用於偵錯工具。 這些物件檔案和內建的可執行檔可以大幅超過任何偵錯資訊的檔案。 符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。 會不產生任何 PDB 檔案。

協力廠商程式庫的偵錯版本的散發者，還有沒有 PDB 檔案的優點。 不過，任何先行編譯標頭的物件檔案所需的程式庫連結階段期間，並進行偵錯。 如果只輸入.pch 目的檔中的資訊 （和任何程式碼） 時，您也必須使用[/Yl （插入偵錯程式庫的 PCH 參考）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)選項，當您建置程式庫時，根據預設，已啟用。

[/Gm （啟用最少重建）](../../build/reference/gm-enable-minimal-rebuild.md)選項時，不提供 **/z7**指定。

### <a name="zi"></a>/ZI

**/Zi**選項會產生個別的 PDB 檔案，其中包含所有符號偵錯資訊用於偵錯工具。 偵錯資訊不包含在目的檔或可執行檔，使其更小。

利用 **/Zi**並不會影響最佳化。 不過， **/Zi**的確 **/ 偵錯**; 請參閱[/DEBUG （產生偵錯資訊）](../../build/reference/debug-generate-debug-info.md)如需詳細資訊。

當您同時指定兩者 **/Zi**並 **/clr**，則<xref:System.Diagnostics.DebuggableAttribute>屬性不放在組件中繼資料。 如果您想要它，您必須在原始程式碼中指定它。 這個屬性可能影響應用程式的執行階段效能。 如需有關如何**Debuggable**屬性會影響效能，以及如何在您可以修改的效能影響，請參閱[使映像更容易偵錯](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。

編譯器名稱 PDB 檔案*專案*.pdb。 如果您編譯專案外的檔案時，編譯器會建立 PDB 檔名為 VC*x*.pdb，其中*x*串連中使用的編譯器版本的主要和次要的版本號碼。 編譯器會使用此選項時，偵錯工具指向符號和行號資訊的位置建立每個目的檔中內嵌 PDB 和識別的時間戳記簽章的名稱。 名稱和 PDB 檔案中的簽章必須符合在偵錯工具中載入符號的可執行檔。 WinDBG 偵錯工具可以使用載入不相符的符號`.symopt+0x40`命令。 Visual Studio 並沒有類似的選項，來載入不相符的符號。

如果您從使用已編譯的物件建立程式庫 **/Zi**，當程式庫連結至程式時，關聯的.pdb 檔案必須是可用。 因此，如果您要散發程式庫，您也必須散發 PDB 檔案。 若要建立不使用 PDB 檔案包含偵錯資訊的程式庫，您必須選取 **/z7**選項。 如果您使用先行編譯標頭選項，先行編譯標頭和原始碼的其餘部分偵錯資訊被放在 PDB 檔案。

### <a name="zi"></a>/ZI

**/ZI**選項很相似 **/Zi**，但它會產生的 PDB 檔案格式可支援[編輯後繼續](/visualstudio/debugger/edit-and-continue-visual-cpp)功能。 若要使用 編輯後繼續 」 偵錯功能，您必須使用此選項。 [編輯後繼續] 功能可用於開發人員生產力，但可能會導致程式碼大小、 效能和編譯器一致性問題。 由於大部分最佳化都與 編輯後繼續不相容，使用 **/ZI**停用任何`#pragma optimize`程式碼中的陳述式。 **/ZI**也會使用與不相容選項[ &#95;&#95;行&#95;&#95;預先定義的巨集](../../preprocessor/predefined-macros.md); 使用程式碼編譯 **/ZI**不能使用 **&#95;&#95;行&#95;&#95;** 當做非類型樣板引數，雖然 **&#95;&#95;行&#95;&#95;** 可用巨集展開中。

**/ZI**選項會強制兩者[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md)並[/FC （完整路徑的來源診斷中原始程式碼檔）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)使用您所編譯的選項。

**/ZI**與不相容[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

> [!NOTE]
> **/ZI**選項僅供以 x86 和 x64 處理器為目標的編譯器以; 這個編譯器選項不適用於以 ARM 處理器為目標的編譯器。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 開啟**組態屬性** > **C/c + +** > **一般**屬性頁。

1. 修改**偵錯資訊格式**屬性。 選擇**確定**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)

