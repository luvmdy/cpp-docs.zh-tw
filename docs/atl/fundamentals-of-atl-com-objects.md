---
title: ATL COM 物件的基本概念
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 6af732b381ab0c6c507d1d651b096e3976ab2d4b
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176493"
---
# <a name="fundamentals-of-atl-com-objects"></a>ATL COM 物件的基本概念

下圖說明的類別和介面，可用來定義 ATL COM 物件之間的關聯性。

![ATL 結構](../atl/media/vc307y1.gif "ATL 結構")

> [!NOTE]
>  此圖表會顯示`CComObject`衍生自`CYourClass`而`CComAggObject`並`CComPolyObject`包含`CYourClass`做為成員變數。

有三種方式，來定義 ATL COM 物件。 標準的選項是使用`CComObject`類別衍生自`CYourClass`。 第二個選項是使用建立彙總的物件`CComAggObject`類別。 第三個選項是使用`CComPolyObject`類別。 `CComPolyObject` 做為混合式： 一樣`CComObject`類別或`CComAggObject`類別，根據第一次建立方式。 如需有關如何使用`CComPolyObject`類別，請參閱[CComPolyObject 類別](../atl/reference/ccompolyobject-class.md)。

當您使用標準的 ATL COM 時，您會使用兩個物件： 外部的物件與內部物件。 外部用戶端會存取內部物件的功能，透過包裝函式中的外部物件所定義。 外部物件屬於下列類型`CComObject`。

當您使用的彙總的物件時，則外部物件不會提供包裝函式內部物件的功能。 相反地，則外部物件會提供可直接存取的外部用戶端的指標。 在此案例中，則外部物件為類型`CComAggObject`。 內部物件是外部物件的成員變數，而且它的類型是`CYourClass`。

因為用戶端沒有瀏覽要互動的內部物件的外部物件，則彙總的物件會是通常更有效率。 此外，則外部物件不必知道物件之功能的彙總，彙總物件的介面是可以直接提供給用戶端。 不過，並非所有物件都可以加以彙都總。 要彙總物件，它必須記住的彙總設計。

實作 ATL [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)分成兩個階段：

- [CComObject](../atl/reference/ccomobject-class.md)， [CComAggObject](../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../atl/reference/ccompolyobject-class.md)實作`IUnknown`方法。

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理的參考計數和外部的指標`IUnknown`。

其他類別會處理您的 ATL COM 物件的其他層面：

- [CComCoClass](../atl/reference/ccomcoclass-class.md)定義物件的預設類別的 factory 和彙總模型。

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的預設實作`IDispatch Interface`任何物件上的雙重介面的一部分。

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)實作`ISupportErrorInfo`介面，以確保錯誤資訊可傳播呼叫鏈結正確。

## <a name="in-this-section"></a>本節內容

[實作 CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
顯示的範例實作的 COM 對應項目`CComObjectRootEx`。

[實作 CComObject、CComAggObject 和 CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
討論如何**DECLARE_\*_AGGREGATABLE**巨集，會影響使用`CComObject`， `CComAggObject`，和`CComPolyObject`。

[支援 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
列出用於支援的 ATL 實作類別`IDispatch`和`IErrorInfo`介面。

[支援 IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
討論的步驟來實作您類別的連接點。

[變更預設 Class Factory 和彙總模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
顯示用來變更預設的類別處理站和彙總模型哪些巨集。

[建立彙總物件](../atl/creating-an-aggregated-object.md)<br/>
列出用於建立彙總的物件的步驟。

## <a name="related-sections"></a>相關章節

[建立 ATL 專案](../atl/reference/creating-an-atl-project.md)<br/>
提供建立 ATL COM 物件的相關資訊。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)

