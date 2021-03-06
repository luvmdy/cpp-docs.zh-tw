---
title: /WINMDKEYFILE (指定 winmd 金鑰檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 076533278bb9b8ec2838cfb719bcb4df1784b258
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436786"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (指定 winmd 金鑰檔)

指定金鑰或金鑰組簽署 Windows 執行階段中繼資料 (.winmd) 檔案。

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>備註

類似於[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)套用到.winmd 檔案的連結器選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取  **Windows 中繼資料**屬性頁。

1. 在  **Windows 中繼資料金鑰檔**方塊中，輸入檔案位置。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)