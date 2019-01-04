---
title: IDebugPortSupplier2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9672ead8b774761d5655acc86878103664f8662f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841454"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Obtém uma porta de um fornecedor de porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidPort`  
 [in] Identificador global exclusivo (GUID) da porta.  
  
 `ppPort`  
 [out] Retorna um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa a porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_PORTSUPPLIER_NO_PORT` se nenhuma porta existir com o identificador fornecido.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)