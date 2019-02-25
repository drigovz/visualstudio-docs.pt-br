---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58684cc5139d2797a08b74d9c0309252141e2498
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723390"
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