---
title: 'IEnumDebugThreads2:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8553ae1c75bd8b5716182485f0b0dc8d77da14f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147728"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna o próximo conjunto de elementos da enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugThread2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugThread2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de elementos a serem recuperados. Também especifica o tamanho máximo da `rgelt` matriz.  
  
 `rgelt`  
 [entrada, saída] Matriz de elementos [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) a ser preenchida.  
  
 `pceltFetched`  
 fora Retorna o número de elementos realmente retornados em `rgelt` .  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos puder ser retornado; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
