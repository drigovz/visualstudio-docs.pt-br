---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c1f30c3a465d4803e5c91f14ee45ad582e76d986
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58921819"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa uma posição em um arquivo de origem como um deslocamento de caractere.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implementado pelo IDE e consumido por mecanismos de depuração.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugDocumentPositionOffset2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera o intervalo para a posição atual do documento.|  
  
## <a name="remarks"></a>Comentários  
 Isso retorna as mesmas informações que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , mas na `char` deslocamentos do início do documento. Isso apresenta o documento como ele deve existir em um disco, ou seja, uma matriz unidimensional de caracteres, em vez das informações de linha e coluna que normalmente é retornado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
