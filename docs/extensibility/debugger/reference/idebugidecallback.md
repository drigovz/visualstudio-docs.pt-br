---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83243899bdc11c58e76c35b6d9eb7b9555794374
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838650"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Permite que um avaliador de expressão (EE) exiba uma mensagem na janela de saída do depurador.

## <a name="syntax"></a>Sintaxe

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esse retorno de chamada é implementado pelo mecanismo de depuração gerenciado.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ele pode ser consumido por um avaliador de expressão para enviar a saída para a janela de saída do depurador.

## <a name="methods"></a>Métodos
 Essa interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envia a cadeia de caracteres da mensagem especificada para a janela de saída do depurador.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
