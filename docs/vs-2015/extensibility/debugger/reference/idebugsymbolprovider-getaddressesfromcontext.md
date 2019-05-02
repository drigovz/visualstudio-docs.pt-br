---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebd36bdda5059a4fd3c0334a5a2f222aaae40f01
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922557"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método mapeia um contexto de documento em uma matriz de endereços de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
