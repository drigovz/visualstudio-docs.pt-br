---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727831"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Habilita que um avaliador de expressão (EE) exiba uma mensagem na janela de saída do depurador.

## <a name="syntax"></a>Sintaxe

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Este retorno de chamada é implementado pelo mecanismo de depuração gerenciado.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ele pode ser consumido por um avaliador de expressão para enviar saída para a janela de saída do depurador.

## <a name="methods"></a>Métodos
 Esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envia a seqüência de mensagens especificada para a janela de saída do depurador.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
