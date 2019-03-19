---
title: IDebugAsyncOperation Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150810"
---
# <a name="idebugasyncoperation-interface"></a>Interface IDebugAsyncOperation
O Gerenciador de depuração do processo implementa o `IDebugAsyncOperation` interface. Um mecanismo de linguagem chama o `IDebugApplication::CreateAsyncDebugOperation` método para obter uma referência a esta interface. O mecanismo de linguagem pode usar o `IDebugAsyncOperation` interface para fornecer acesso assíncrono a uma operação de depuração síncrona.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugAsyncOperation` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Retorna a operação de depuração síncrona associada a este objeto.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Faz com que a operação assíncrona começar.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Cancela uma operação.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Determina se a operação de depuração foi concluída.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Fornece o valor de retorno e parâmetro de objeto de retorno da operação de depuração síncrona.|