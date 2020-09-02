---
title: 'IDebugInterceptExceptionCompleteEvent2:: GetInterceptCookie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e186419a102bdf48a437002ab03120587d6e0822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180647"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Chamado quando o processamento de uma exceção interceptada foi concluído.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pqwCookie`  
 fora Valor exclusivo que é associado à exceção que foi interceptada.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que o método [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) tiver concluído o tratamento de uma exceção interceptada, ele enviará o evento [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) . O manipulador pode usar o `GetInterceptCookie` método para recuperar o valor exclusivo associado à exceção (o mesmo valor passado para o `InterceptCurrentException` método).  
  
## <a name="see-also"></a>Consulte Também  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
