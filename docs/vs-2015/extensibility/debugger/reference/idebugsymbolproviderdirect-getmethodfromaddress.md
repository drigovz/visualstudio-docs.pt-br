---
title: 'IDebugSymbolProviderDirect:: GetMethodFromAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 16ba628887f1910738df825a0965959715c5d250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155109"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera informações sobre o método no endereço de depuração especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 no Endereço de depuração que é representado pela interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pGuid`  
 fora Identificador exclusivo do módulo.  
  
 `pAppID`  
 fora Identificador do domínio do aplicativo.  
  
 `pTokenClass`  
 fora O token que representa a classe que a contém.  
  
 `pTokenMethod`  
 fora Token que representa o módulo.  
  
 `pdwOffset`  
 fora Um deslocamento em bytes do início do `pAddress` parâmetro.  
  
 `pdwVersion`  
 fora Número de versão do método.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
