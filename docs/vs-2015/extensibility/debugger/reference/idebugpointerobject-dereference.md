---
title: IDebugPointerObject::D eReference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40a0e66e5f3cb3a50618a3c8dd4fd5926c34c624
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201000"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o objeto apontado para.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwIndex`  
 no Um deslocamento de byte simples do início do objeto apontado para.  
  
 `ppObject`  
 fora Retorna um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o objeto apontado para, além de offset, se houver.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro. Retorna E_FAIL se esse objeto não apontar para outro objeto.  
  
## <a name="remarks"></a>Comentários  
 O objeto apontado pode ser um tipo primitivo ou mais complexo, como uma classe ou estrutura.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
