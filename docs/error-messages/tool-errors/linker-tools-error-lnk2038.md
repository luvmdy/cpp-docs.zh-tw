---
title: 連結器工具錯誤 LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: a22b31f1ac3226271ed7ff03b5be7dad7fff6b93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594307"
---
# <a name="linker-tools-error-lnk2038"></a>連結器工具錯誤 LNK2038

> 偵測到不相符的 '*名稱*': 值'*value_1*'不符合值'*value_2*' 在*filename.obj*

連結器偵測到符號不相符。 此錯誤表示應用程式，包括程式庫或其他物件的不同部分程式碼應用程式連結，以使用符號的衝突的定義。 [偵測到不符](../../preprocessor/detect-mismatch.md)pragma 用來定義這類符號和偵測其衝突的值。

## <a name="possible-causes-and-solutions"></a>可能原因和解決方案

在專案的目的檔過期時，會發生這個錯誤。 在您嘗試解決這個錯誤的其他方案之前，執行乾淨的組建以確保目的檔是最新的。

Visual Studio 會定義下列符號以防止連結不相容的程式碼，此程式碼可能會造成執行階段錯誤或其他未預期的行為。

- `_MSC_VER` 表示用來建置應用程式庫的 Visual c + + 編譯器的主要和次要的版本號碼。 使用其中一個版本的 Visual C++編譯器編譯的程式碼與使用主要和次要版本號碼不同的編譯器編譯的程式碼不相容。 如需詳細資訊，請參閱 <<c0> `_MSC_VER` 中[預先定義的巨集](../../preprocessor/predefined-macros.md)。

   如果您要連結到與您使用，而且您無法取得，或建置程式庫的相容版本的 Visual c + + 編譯器的版本不相容的程式庫，您可以使用較早版本的編譯器來建置您的專案： 變更<c1/>平台工具組**舊版工具組專案屬性。 如需詳細資訊，請參閱 <<c0> [ 如何： 修改目標 Framework 和平台工具組](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

- `_ITERATOR_DEBUG_LEVEL` 表示層級的安全性和偵錯 c + + 標準程式庫中啟用的功能。 這些功能可以變更某些 C++ 標準程式庫物件的表示，因而使它們與使用其他安全性和偵錯功能的項目不相容。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)。

- `RuntimeLibrary` 指出由應用程式或程式庫的 c + + 標準程式庫和 C 執行階段版本。 使用 C++ 標準程式庫或 C 執行階段某個版本的程式碼與使用不同版本的程式碼不相容。 如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](../../build/reference/md-mt-ld-use-run-time-library.md)。

- `_PPLTASKS_WITH_WINRT` 表示會使用該程式碼[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)連結至使用不同的設定所編譯的物件[/ZW](../../build/reference/zw-windows-runtime-compilation.md)編譯器選項。 (**/ZW**支援 C + + /CX。)使用或依賴 PPL 的程式碼必須使用相同的編譯 **/ZW**應用程式的其餘部分中使用的設定。

請確認這些符號值在您的 Visual Studio 方案的專案中一致，而且它們也與應用程式所連結的程式碼和程式庫一致。

## <a name="third-party-library-issues-and-vcpkg"></a>協力廠商程式庫問題和 Vcpkg

如果您嘗試將協力廠商程式庫設定為組建的一部分時，您會看到此錯誤，請考慮使用[Vcpkg](../../vcpkg.md)，Visual c + + 套件管理員安裝及建置程式庫。 Vcpkg 支援大量且不斷成長[協力廠商程式庫清單](https://github.com/Microsoft/vcpkg/tree/master/ports)，並設定所有組態屬性和相依性所需的建置成功，為您專案的一部分。 如需詳細資訊，請參閱相關[Visual c + + 部落格](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)張貼。

## <a name="see-also"></a>另請參閱

[連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)