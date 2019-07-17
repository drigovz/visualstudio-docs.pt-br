---
title: IDebugFunctionObject2::Evaluate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c25e62dbfc0778fb1bf07c9108c9111f3520d87f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180964"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Chama a função e retorna o valor resultante como um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppParams`  
 [in] Uma matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representam os parâmetros de entrada. Cada um desses parâmetros foi criada usando um dos métodos Create nessa interface.  
  
 `dwParams`  
 [in] O número de parâmetros no `ppParams` matriz.  
  
 `dwEvalFlags`  
 [in] Uma combinação de sinalizadores do [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeração que especificam como a avaliação deve ser executada.  
  
 `dwTimeout`  
 [in] Especifica o tempo máximo, em milissegundos, para aguardar antes de retornar do método. Use **infinito** para aguardar indefinidamente.  
  
 `ppResult`  
 [out] Retorna um **IDebugObject** que representa o valor da função como um objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
