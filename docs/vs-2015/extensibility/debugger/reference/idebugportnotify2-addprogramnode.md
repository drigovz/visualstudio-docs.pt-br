---
title: 'IDebugPortNotify2:: AddProgramNode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::AddProgramNode
helpviewer_keywords:
- IDebugPortNotify2::AddProgramNode
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f96a76b7e9cf10c571ab1b9fac92e514ccfbeeb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188429"
---
# <a name="idebugportnotify2addprogramnode"></a>IDebugPortNotify2::AddProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Registra um programa que pode ser depurado com a porta em que está sendo executado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT AddProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int AddProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProgramNode`  
 no Um objeto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representa o programa a ser registrado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um nó de programa pode ter o registro cancelado da porta chamando o método [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
