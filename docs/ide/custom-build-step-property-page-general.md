---
title: 自訂建置步驟屬性頁：一般
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: dc6765c9519c6cdb4245afa2f07079548a07e1fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621750"
---
# <a name="custom-build-step-property-page-general"></a>自訂建置步驟屬性頁：一般

對於專案中每個專案組態和目標平台的組合，您可以指定建置專案時要執行的自訂步驟。

如需此頁面的 Linux 版本，請參閱[自訂建置步驟屬性 (Linux C++)](../linux/prop-pages/custom-build-step-linux.md)。

## <a name="uielement-list"></a>UIElement 清單

- **命令列**

   會由自訂建置步驟執行的命令。

- **描述**

   當自訂建置步驟執行時所顯示的訊息。

- **輸出**

   自訂建置步驟所產生的輸出檔。 必須要有這項設定，累加建置才能正常運作。

- **其他相依性**

   用於自訂建置步驟之任何其他輸入檔以分號分隔的清單。

- **後執行與先執行**

   這些選項定義自訂建置步驟在建置流程中執行的時間點 (相對於所列出的目標)。 最常列出的目標是 BuildGenerateSources、BuildCompile 和 BuildLink，因為這些目標代表建置流程中的主要步驟。 其他常列目標包括 Midl、CLCompile 和 Link。

- **將輸出視為內容**

   此選項在通用 Windows 平台或 Windows Phone 應用程式中才有用處，其所有內容檔都包含在 .appx 套件中。

### <a name="to-specify-a-custom-build-step"></a>指定自訂建置步驟

1. 在功能表列上，依序選擇 [專案] 和 [屬性]。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

1. 在 [屬性頁] 對話方塊中，巡覽至 [組態屬性]、[自訂建置步驟]、[一般] 頁面。

1. 修改設定。

## <a name="see-also"></a>請參閱

[屬性頁](../ide/property-pages-visual-cpp.md)