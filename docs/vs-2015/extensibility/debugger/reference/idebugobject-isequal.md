---
title: 'IDebugObject:: IsEqual | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85252cdaf9fb076ebd4f8000115bcea576531bb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159117"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Compara um objeto com este objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pObject`  
 no Um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o objeto a ser comparado.  
  
 `pfIsEqual`  
 fora Retornará um valor diferente de zero ( `TRUE` ) se os valores dos objetos forem iguais; caso contrário, retornará zero ( `FALSE` ).  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, esse método pode comparar os endereços dos valores representados pelo `pObject` parâmetro e esse objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; se os endereços forem iguais, os objetos poderão ser considerados iguais.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
