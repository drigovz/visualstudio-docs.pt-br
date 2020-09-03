---
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08483d5f015af7088eb5968a5bf6358ce5065579
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179470"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria um objeto usando um construtor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 no Um objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que representa o construtor do objeto a ser criado.  
  
 `dwArgs`  
 no O número de parâmetros na `pArg` matriz. Representa o número de parâmetros passados para o construtor.  
  
 `pArg`  
 no Uma matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa os parâmetros passados para o construtor.  
  
 `ppObject`  
 fora Retorna um `IDebugObject` representando o objeto recém-criado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método para criar um objeto que represente uma instância de uma classe (ou outro tipo complexo que exija um construtor) que seja um parâmetro para a função que é representada pela interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 Se o parâmetro de objeto não exigir um construtor, chame o método [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
