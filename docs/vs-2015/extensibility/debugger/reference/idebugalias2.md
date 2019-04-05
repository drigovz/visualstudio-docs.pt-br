---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2349203c49bc164bb3af6bcf51e39afb56022be0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926972"
---
# <a name="idebugalias2"></a>IDebugAlias2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa um alias de numérico para uma variável e permite que um avaliador de expressão (EE) para obter o domínio do aplicativo para o alias.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelo mecanismo de depuração gerenciados (DES).  
  
## <a name="methods"></a>Métodos  
 Além dos métodos na [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface, essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera o identificador para o domínio de aplicativo.|  
  
## <a name="remarks"></a>Comentários  
 Um alias é um número decimal no formulário de cadeia de caracteres seguido pelo caractere #, por exemplo, # 1001.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: EE.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
