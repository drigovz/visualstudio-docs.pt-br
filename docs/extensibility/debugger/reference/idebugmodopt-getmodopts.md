---
title: IDebugModOpt::GetModOpts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c611c55654ee14bc3cda3f27fe20e19188faa71a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017157"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Recupera uma lista de modificadores opcionais.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Número de elementos a serem retornados.  
  
 `rgelt`  
 [out] Retorna uma matriz que contém as opções.  
  
 `pceltFetched`  
 [no, out] Número de elementos retornados no `rgelt` matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)