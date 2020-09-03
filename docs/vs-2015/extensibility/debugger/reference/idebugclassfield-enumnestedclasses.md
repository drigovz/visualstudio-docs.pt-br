---
title: 'IDebugClassField:: EnumNestedClasses | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7745eea3f5b3264016a25defd696a9b85f2e9fb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191079"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria um enumerador para as classes aninhadas nesta classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 fora Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa a lista de classes aninhadas. Retorna um valor nulo se não houver nenhuma classe aninhada.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver classes aninhadas. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que descreve uma classe aninhada.  
  
 Uma classe aninhada é uma classe definida dentro de outra classe. Por exemplo:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 A enumeração [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) conterá um objeto que representa a `NestedClass` classe.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
