---
title: ptr::~ptr
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr.com.ptr.~ptr
- ptr.~ptr
- msclr::com.ptr::~ptr
- ~ptr
- ptr::~ptr
helpviewer_keywords:
- ptr::~ptr
ms.assetid: 5f644aa5-fe66-4992-a5f8-13ec1292c949
ms.openlocfilehash: 452876fb2b377048b3916e61d39467e2279cd4ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618060"
---
# <a name="ptrptr"></a>ptr::~ptr

Destructs `com::ptr`。

## <a name="syntax"></a>語法

```
~ptr();
```

## <a name="remarks"></a>備註

在終結時`com::ptr`釋放它擁有與其 COM 物件的所有參考。 假設不有任何其他 COM 物件所持有的參考，將刪除的 COM 物件，並釋放其記憶體。

## <a name="example"></a>範例

這個範例實作 CLR 類別，此類別使用 `com::ptr` 來包裝其私用成員 `IXMLDOMDocument` 物件。  在 `main`函式，這兩個`XmlDocument`在超出範圍時，就會呼叫物件的解構函式`try`區塊中，導致基礎`com::ptr`解構函式所呼叫，釋出所有已擁有的參考，以與 COM物件。

```
// comptr_dtor.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\com\ptr.h >

**命名空間**msclr::com

## <a name="see-also"></a>另請參閱

[ptr 成員](../dotnet/ptr-members.md)<br/>
[ptr::ptr](../dotnet/ptr-ptr.md)<br/>
[ptr::CreateInstance](../dotnet/ptr-createinstance.md)