---
title: /MP (使用多處理序建置)
ms.date: 02/22/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MultiProcessorCompilation
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
ms.openlocfilehash: d0a3e50ca75535d505e46c0e454a8e0902b1ffb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562080"
---
# <a name="mp-build-with-multiple-processes"></a>/MP (使用多處理序建置)

**/MP** 選項可縮短在命令列上編譯原始程式檔的總時間。 **/MP** 選項可讓編譯器在不同的處理序中，建立一或多個本身的複本。 然後這些複本會同時編譯原始程式檔， 使得建置原始程式檔的總時間大幅地降低。

## <a name="syntax"></a>語法

> **/MP**[*processMax*]

## <a name="arguments"></a>引數

*processMax*<br/>
(選擇性) 編譯器可建立的處理序數目上限。

*ProcessMax*引數的範圍必須介於 1 到 65536。 否則，編譯器會發出警告訊息**D9014**，會忽略*processMax*引數，並假設處理序數目上限為 1。

如果您省略*processMax*引數，編譯器會擷取數目[有效的處理器](#effective_processors)從作業系統中，您電腦上，並建立每個處理器的處理序。

## <a name="remarks"></a>備註

**/MP** 編譯器選項可以讓您在編譯許多檔案時，大幅縮短建置時間。 若要改善建置時間，編譯器會建立最多*processMax*本身的複本，然後使用這些複本同時編譯原始程式檔。 **/MP** 選項適用於編譯，但不適用於連結或連結時產生程式碼。 **/MP** 選項預設為關閉。

建置時間的改善取決於電腦上的處理器數目、要編譯的檔案數目、系統資源的可用性 (例如 I/O 容量) 等因素而定。 您可以使用 **/MP** 選項來進行實驗，以決定建置特定專案的最佳設定。 如需協助制定決策的相關建議，請參閱 [方針](#guidelines)。

## <a name="incompatible-options-and-language-features"></a>不相容的選項和語言功能

**/MP** 選項與某些編譯器選項和語言功能不相容。 如果您使用的不相容的編譯器選項和 **/MP**選項，則編譯器會發出警告**D9030** ，並忽略 **/MP**選項。 如果您使用不相容的語言功能時，編譯器會發出錯誤[C2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md)然後結束或繼續視目前編譯器警告層級的選項。

> [!NOTE]
> 大部分的選項都不相容，這是因為如果允許這些選項，在同時執行編譯器時就會將編譯器的輸出一起寫入主控台或特定檔案中。 結果，輸出就會相互摻雜而且不完整。 有時候，結合選項還可能會使效能變得更差。

下表列出與 **/MP** 選項不相容的編譯器選項和語言功能：

|選項或語言功能|描述|
|--------------------------------|-----------------|
|[#import](../../preprocessor/hash-import-directive-cpp.md) 前置處理器指示詞|將類型程式庫中的類型轉換成 C++ 類別，然後將這些類別寫入標頭檔。|
|[/E](../../build/reference/e-preprocess-to-stdout.md)、 [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|將前置處理器輸出複製到標準輸出 (**stdout**)。|
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|允許累加式重建。|
|[/showIncludes](../../build/reference/showincludes-list-include-files.md)|將 Include 檔案的清單寫入標準錯誤 (**stderr**)。|
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|寫入先行編譯的標頭檔。|

## <a name="diagnostic-messages"></a>診斷訊息

如果您指定與 **/MP** 選項不相容的選項或語言功能，就會收到診斷訊息。 下表列出編譯器的訊息和行為：

|診斷訊息|描述|編譯器行為|
|------------------------|-----------------|-----------------------|
|**C2813**|**#Import** 指示詞與 **/MP** 選項不相容。|除非另外指定 [編譯器警告層級](../../build/reference/compiler-option-warning-level.md) 選項，否則編譯就會結束。|
|**D9014**|指定無效的值*processMax*引數。|編譯器會忽略無效值，並假設值為 1。|
|**D9030**|指定的選項與 **/MP**不相容。|編譯器會忽略 **/MP** 選項。|

## <a name="guidelines"></a> 方針

### <a name="measure-performance"></a>測量效能

請使用總建置時間來測量效能。 您可以使用實體時鐘來計算建置時間，或使用軟體來計算建置開始到停止之間的時間差。 如果您的電腦有多個處理器，則以實體時鐘計算出來的時間可能比軟體時間測量更精確。

### <a name="effective_processors"></a> Effective Processors

一部電腦都可以有一或多個虛擬處理器，也稱為*有效的處理器*，每一個實體處理器。 此外，每一個實體處理器都可以有一或多個核心，如果作業系統啟用核心的超執行緒，則每一個核心看起來都會有兩個虛擬處理器。

例如，如果電腦有一個實體處理器，而處理器有一個核心且停用超執行緒，則該電腦會有一個有效的處理器。 相反地，如果電腦有兩個實體處理器，每一個都有兩個核心，且所有核心都啟用超執行緒，則這部電腦就有八個有效的處理器。 也就是說，（8 有效的處理器） = （2 個實體處理器） x （2 核心，每個實體處理器） x （2 個有效的處理器每個核心，因為超執行緒）。

如果您省略*processMax*中的引數 **/MP**選項，編譯器會從作業系統中，取得有效處理器的數目，並接著會建立每個有效處理器的其中一個處理序。 不過，編譯器無法保證哪個處理序會在特定處理器上執行，因為這是由作業系統決定。

### <a name="number-of-processes"></a>處理序數目

編譯器會計算要用來編譯原始程式檔的處理序數目。 您在命令列上所指定的原始程式檔數目，以及使用 **/MP** 選項明確或隱含指定的處理序數目，兩者中較小的那個數目就是處理序的數目值。 如果您提供，您可以明確設定處理序數目上限*processMax*引數 **/MP**選項。 或者您可以使用預設值，也就是有效的處理器數目在電腦上，如果您省略*processMax*引數。

例如，假設您指定下列命令列：

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

在此情況下，編譯器會使用五個處理序，因為五個原始程式檔和最多七個處理序這兩個數字中，這是較小的數目。 或者，假設您的電腦有兩個有效的處理器，而且您指定下列命令列：

`cl /MP a.cpp b.cpp c.cpp`

此時，作業系統會回報有兩個處理器，因此編譯器會在計算中使用兩個處理序。 如此一來，編譯器會使用兩個處理序來執行建置，因為兩個處理序和三個原始程式檔這兩個數字中，這是較小的數目。

### <a name="source-files-and-build-order"></a>原始程式檔和建置順序

原始程式檔編譯的順序，可能和它們出現在命令列中的順序不同。 雖然編譯器會建立一組處理序，其中包含編譯器的複本，但是作業系統會為每一個處理序的執行時間進行排程。 因此，您無法保證原始程式檔會以特定順序編譯。

當處理序可用來編譯時，就會編譯原始程式檔。 如果檔案比處理序還多，可用的處理序就會編譯第一組檔案。 當處理序處理完上一個檔案，還可以接著處理剩下的其中一個檔案時，就會處理剩下的檔案。

請不要在命令列上多次指定相同的原始程式檔。 例如，當工具自動建立以專案相依性資訊為依據的 [makefile](../../build/contents-of-a-makefile.md) 時，就可能會發生這種情況。 如果您不指定 **/MP** 選項，則編譯器會依序處理檔案清單，並重新編譯檔案。 但是，如果您指定 **/MP** 選項，則不同的編譯器可能會同時編譯相同的檔案。 如此一來，不同的編譯器會同時嘗試寫入同一個輸出檔。 其中一個編譯器會取得輸出檔的獨佔寫入權限並成功完成作業，而另一個編譯器則會失敗並發生檔案存取錯誤。

### <a name="using-type-libraries-import"></a>使用類型程式庫 (#import)

編譯器不支援使用 [#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞搭配 **/MP** 參數。 如果可能，請遵循下列步驟來解決這個問題：

- 將各原始程式檔中的所有 `#import` 指示詞移至一或多個檔案，然後不使用 **/MP** 選項來編譯這些檔案。 結果會產生一組標頭檔。

- 在剩下的原始程式檔中，插入 [#include](../../preprocessor/hash-include-directive-c-cpp.md) 指示詞 (指定產生的標頭)，然後使用 **/MP** 選項編譯剩下的原始程式檔。

### <a name="visual-studio-project-settings"></a>Visual Studio 專案設定

#### <a name="the-msbuildexe-tool"></a>MSBUILD.exe 工具

Visual Studio 會使用[MSBuild.exe](/visualstudio/msbuild/msbuild-reference)工具來建置方案和專案。 **/Maxcpucount:**_數目_(或 **/m:**_數目_) MSBuild.exe 工具的命令列選項可建置在多個專案相同的時間。 而 **/MP** 編譯器選項可同時建置多個編譯單位。 如果應用程式適用的話，請使用 **/MP** 及/或 **/maxcpucount**來改善您的方案建置時間。

您的方案建置時間有一部分取決於執行組建的處理序數目。 *數字*引數[/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) MSBuild 選項會指定要同時建置的專案數目上限。 同樣地， *processMax*引數 **/MP**編譯器選項會指定要同時建置的編譯單位的數目上限。 如果 **/maxcpucount**選項會指定*P*專案並 **/MP**選項指定*C*處理時，最多*P* x *C*在同一時間執行的處理程序。

決定是否要使用 MSBuild 的指導方針或 **/MP**技術如下所示：

- 如果有與每個專案中的幾個檔案的許多專案，使用 MSBuild 工具。

- 如果每個專案內的少數專案有許多檔案，請使用 **/MP** 選項。

- 如果專案和每個專案的檔案數目很平均，使用這兩個 MSBuild 和 **/MP**。 一開始，請將 **/maxcpucount** 選項設定為要建置的專案數目，再將 **/MP** 選項設定為電腦上的處理器數目。 測量效能然後調整設定，以產生最佳結果。 重複這個循環，直到您滿意總建置時間為止。

#### <a name="the-gm-compiler-option"></a>/Gm 編譯器選項

根據預設，專案建置會啟用偵錯組建的 **/Gm** 編譯器選項 (累加建置)，而停用發行組件的這個選項。 因此，偵錯組建中的 **/MP** 編譯器選項會自動停用，因為這個選項和預設的 **/Gm** 編譯器選項衝突。

## <a name="see-also"></a>另請參閱

[#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)<br/>
[命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/Zf (PDB 產生速度加快)](zf.md)<br/>
