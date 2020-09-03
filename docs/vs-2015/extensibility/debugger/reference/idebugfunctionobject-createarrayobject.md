---
title: 'IDebugFunctionObject:: createarrayobject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205817"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria um objeto de matriz. Essa matriz pode conter valores primitivos ou de instância de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ot`  
 no Especifica um valor da enumeração de [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) indicando o tipo do novo objeto de matriz.  
  
 `pClassField`  
 no Um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa a classe de um objeto, se estiver criando uma matriz de valores de instância de objeto. Se estiver criando uma matriz de objetos primitivos, esse parâmetro será um valor nulo.  
  
 `dwRank`  
 no A classificação ou o número de dimensões da matriz.  
  
 `dwDims`  
 no Os tamanhos de cada dimensão da matriz.  
  
 `dwLowBounds`  
 no A origem de cada dimensão (normalmente 0 ou 1).  
  
 `ppObject`  
 fora Retorna um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa a matriz recém-criada. Isso é, na verdade, um objeto [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método para criar um objeto que representa um parâmetro de matriz para a função que é representada pela interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
