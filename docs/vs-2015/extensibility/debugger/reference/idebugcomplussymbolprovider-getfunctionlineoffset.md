---
title: IDebugComPlusSymbolProvider::GetFunctionLineOffset | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetFunctionLineOffset
- GetFunctionLineOffset
ms.assetid: 51460f5a-4e98-427a-8315-27246e24fb61
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27168387452cf364ecbf51ba648818617fcff3c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828872"
---
# <a name="idebugcomplussymbolprovidergetfunctionlineoffset"></a>IDebugComPlusSymbolProvider::GetFunctionLineOffset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera o endereço dentro de uma função que representa o deslocamento de linha determinada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetFunctionLineOffset(  
   IDebugAddress*  pAddress,   
   DWORD           dwLine,   
   IDebugAddress** ppNewAddress   
);  
```  
  
```csharp  
int GetFunctionLineOffset(  
   IDebugAddress     pAddress,   
   uint              dwLine,   
   out IDebugAddress ppNewAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] Endereço que representa a função.  
  
 `dwLine`  
 [in] Linha de deslocamento do início da função.  
  
 `ppNewAddress`  
 [out] Novo endereço que representa o deslocamento a partir do início da função de linha.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CDebugSymbolProvider** objeto que expõe a [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetFunctionLineOffset(  
    IDebugAddress *pAddress,  
    DWORD dwLine,  
    IDebugAddress **ppNewAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
    DWORD dwOffset;  
    CDebugAddress* paddr = NULL;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetFunctionLineOffset);  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    // Find the first offset for dwLine in the function  
  
    IfFailGo( pModule->GetFunctionLineOffset( address.addr.addr.addrMethod.tokMethod,  
              address.addr.addr.addrMethod.dwVersion,  
              dwLine,  
              &dwOffset ) );  
  
    // Create the new Address  
  
    address.addr.addr.addrMethod.dwOffset = dwOffset;  
    IfNullGo( paddr = new CDebugAddress(address), E_OUTOFMEMORY );  
    IfFailGo( paddr->QueryInterface( __uuidof(IDebugAddress),  
                                     (void**) ppNewAddress ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetFunctionLineOffset, hr);  
    RELEASE( paddr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

