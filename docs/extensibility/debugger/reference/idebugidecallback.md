---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d05b2ab4c4944cbcce7f920f86eec0ca2f93865a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008212"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Permite que um avaliador de expressão (EE) exibir uma mensagem na janela de saída do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Esse retorno de chamada é implementado pelo mecanismo de depuração gerenciada.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Ele pode ser consumido por um avaliador de expressão para enviar a saída para a janela de saída do depurador.  
  
## <a name="methods"></a>Métodos  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envia a cadeia de caracteres de mensagem especificada para a janela de saída do depurador.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: EE.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll