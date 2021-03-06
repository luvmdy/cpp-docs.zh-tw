---
title: 如何： 建立資源 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
ms.openlocfilehash: 75f7f722b354e60b86abdeb9a3f9a01469aefcf8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513684"
---
# <a name="how-to-create-a-resource"></a>如何：建立資源

> [!NOTE]
> **資源檢視**在 Express 版中不支援。

### <a name="to-create-a-new-resource-in-resource-view"></a>在資源檢視中建立新的資源

1. 使用焦點設在.rc 檔中[資源檢視](../windows/resource-view-window.md)，按一下**編輯**功能表，然後選擇 **加入資源**(或以滑鼠右鍵按一下.rc 檔中的**資源檢視** ，然後選擇 **加入資源**從快顯功能表)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 [加入資源對話方塊](../windows/add-resource-dialog-box.md)中，選擇您想要加入至專案的資源類型。

### <a name="to-create-a-new-resource-in-solution-explorer"></a>在方案總管中建立新的資源

1. 在 [ **方案總管**] 中，以滑鼠右鍵按一下專案資料夾並選擇 [ **加入**]，然後在捷徑功能表上按一下 [ **加入資源** ]。

   如果您的專案中還沒有 .rc 檔，這個步驟會建立一個 .rc 檔。 接著，您可以重複此步驟，將特定資源類型加入至新的 .rc 檔。

2. 在 [加入資源對話方塊](../windows/add-resource-dialog-box.md)中，選擇您想要加入至專案的資源類型。

### <a name="to-create-a-new-resource-in-class-view"></a>在類別檢視中建立新的資源

1. 在 [ [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)] 中，以滑鼠右鍵按一下類別並選擇 [ **加入**]，然後從捷徑功能表按一下 [ **加入資源** ]。

2. 在 [加入資源對話方塊](../windows/add-resource-dialog-box.md)中，選擇您想要加入至專案的資源類型。

### <a name="to-create-a-new-resource-from-the-project-menu"></a>從專案功能表建立新的資源

1. 從 [ **專案** ] 功能表中，選擇 [ **加入資源**]。

當您建立新的資源時，Visual c + + 會指派一個唯一的名稱，比方說， `IDD_Dialog1`。 您可以在相關聯的資源編輯器中或在 [ [屬性視窗](/visualstudio/ide/reference/properties-window)] 中編輯資源的屬性，以自訂此資源 ID。

您可以將資源建立為新的預設資源 (不以範本為基礎的資源)，或建立為模仿 [範本](../windows/how-to-use-resource-templates.md)的資源。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)<br/>
[Add Resource Dialog Box](../windows/add-resource-dialog-box.md)