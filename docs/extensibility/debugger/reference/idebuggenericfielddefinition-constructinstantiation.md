---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83284124f4cdf2fce49812998b6444fa43dc958e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954937"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Constrói uma instância do campo considerando uma matriz de argumentos de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cArgs`  
 [in] Número de argumentos no `ppArgs` matriz.  
  
 `ppArgs`  
 [in] Matriz que contém os argumentos de tipo. Os argumentos de tipo devem ser tipos fechados (genéricos não genéricas ou totalmente instanciados).  
  
 `ppConstructedField`  
 [out] Retorna o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface que representa o novo campo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As restrições não são verificadas.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)