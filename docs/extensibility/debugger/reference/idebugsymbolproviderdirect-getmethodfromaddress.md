---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d55b029ac0c99392627d44e9fc33394e5eb744e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998892"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Recupera informações sobre o método no endereço especificado de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] Depurar o endereço que é representado pela [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `pGuid`  
 [out] Identificador exclusivo do módulo.  
  
 `pAppID`  
 [out] Identificador do domínio do aplicativo.  
  
 `pTokenClass`  
 [out] Token que representa a classe continente.  
  
 `pTokenMethod`  
 [out] Token que representa o módulo.  
  
 `pdwOffset`  
 [out] Um deslocamento em bytes desde o início do `pAddress` parâmetro.  
  
 `pdwVersion`  
 [out] Número de versão do método.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)