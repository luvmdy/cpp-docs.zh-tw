---
title: /MANIFEST (建立並存組件資訊清單)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
ms.openlocfilehash: 226deb9e8f7273e122e1b9074d2afca8970fc366
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508052"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (建立並存組件資訊清單)

```
/MANIFEST[:{EMBED[,ID=#]|NO}]
```

## <a name="remarks"></a>備註

/MANIFEST 會指定連結器應該建立並排顯示的資訊清單檔案。 如需有關資訊清單檔案的詳細資訊，請參閱[資訊清單檔案參考](/windows/desktop/SbsCs/manifest-files-reference)。

預設為 /MANIFEST。

/MANIFEST:EMBED 選項指定連結器應該將資訊清單檔內嵌在映像中，做為 RT_MANIFEST 類型的資源。 選擇性 `ID` 參數是資訊清單所要使用的資源 ID。 如果是可執行檔，使用值 1。 如果是 DLL，則使用值 2，讓它可以指定私用相依性。 如果未指定 `ID` 參數，已設定 /DLL 選項時預設值為 2，否則預設值為 1。

從 Visual Studio 2008 開始，可執行檔的資訊清單檔案包含指定使用者帳戶控制 (UAC) 資訊的區段。 如果您指定 /MANIFEST，但不是指定[/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)也不[/DLL](../../build/reference/dll-build-a-dll.md)，UAC 層級設定為預設 UAC 片段*asInvoker*插入資訊清單。 如需有關 UAC 層級的詳細資訊，請參閱 < [/MANIFESTUAC （將 UAC 資訊內嵌在資訊清單中）](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)。

若要變更 UAC 的預設行為，請執行其中一項：

- 指定 /MANIFESTUAC 選項並將 UAC 層級設成所要的值

- 如果不想在資訊清單中產生 UAC 片段，則指定 /MANIFESTUAC:NO 選項

如果您沒有指定 /MANIFEST，但指定[/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)註解，會建立資訊清單檔案。 如果指定 /MANIFEST:NO，就不會建立資訊清單檔。

如果您指定 /MANIFEST，資訊清單檔的名稱將會與您的輸出檔名稱相同，但是 .manifest 會附加在檔案名稱之後。 例如，如果您的輸出檔名稱是 MyFile.exe，資訊清單檔名稱會是 MyFile.exe.manifest。  如果您指定 /MANIFESTFILE:*名稱*，資訊清單的名稱是您在中指定*名稱*。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **資訊清單檔案**屬性頁。

1. 修改**產生資訊清單**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)