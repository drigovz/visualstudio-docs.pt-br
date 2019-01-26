---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7fbea573bf7a62770109b9933a977a3f0dca0e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938667"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Esse método mapeia um contexto de documento em uma matriz de endereços de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDocContext`  
 [in] O contexto do documento.  
  
 `fStatmentOnly`  
 [in] Se for TRUE, limita os endereços de depuração para uma única instrução.  
  
 `ppEnumBegAddresses`  
 [out] Retorna um enumerador para os endereços iniciais de depuração associados com essa linha ou a instrução.  
  
 `ppEnumEndAddresses`  
 [out] Retorna um [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumerador para os endereços de depuração final associados a essa linha ou a instrução.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um contexto de documento normalmente indica um intervalo de linhas de código-fonte. Esse método fornece inicial e endereços de depuração finais associados a essas linhas. Algumas linguagens permitem que as instruções que abrangem várias linhas, ou linhas que contém mais de uma instrução. Esse método fornece um sinalizador para limitar os endereços de depuração para uma única instrução.  
  
 É possível que uma única instrução ter vários endereços de depuração, como no caso de modelos.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)