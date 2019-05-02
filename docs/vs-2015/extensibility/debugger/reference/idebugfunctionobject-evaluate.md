---
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e19baa193bb015056b9e5abde4c7a274f635c0c8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927741"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Chama a função e retorna o valor resultante como um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppParams`  
 [in] Uma matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representam os parâmetros de entrada. Cada um desses parâmetros foi criada com um dos `Create` métodos em de [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
 `dwParams`  
 [in] O número de parâmetros no `ppParams` matriz.  
  
 `dwTimeout`  
 [in] Especifica o tempo máximo, em milissegundos, para aguardar antes de retornar do método. Use `INFINITE` para aguardar indefinidamente.  
  
 `ppResult`  
 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o valor da função como um objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método configura e executa uma chamada de função representada pela [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
