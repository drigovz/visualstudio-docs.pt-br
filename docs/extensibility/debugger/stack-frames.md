---
title: Registros de ativação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de3a0267d366f926fa5705c7455b237cafe4820a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348503"
---
# <a name="stack-frames"></a>Quadros de pilha
Na arquitetura do depurador, uma *quadro de pilha*:

- É uma abstração de uma pilha que fornece o contexto de execução de um thread. Um thread sempre é executado dentro de uma função. Um quadro de pilha contém as variáveis locais da função e os argumentos a ele. Para depurar com o Visual Studio, o idioma ou o ambiente que está sendo depurado deve dar suporte a quadros de pilha.

- Pode tanto identificar e descrever em si e pode retornar o thread associado. Um quadro de pilha também pode retornar o contexto de código que representa o ponteiro de instrução atual e a documentação associada e contextos de avaliação de expressão.

- Tem propriedades que descrevem o nome, tipo e valor de argumentos e variáveis locais, e que aparecem em várias janelas de depuração do IDE.

- É representado por um [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, geralmente criado por um mecanismo de depuração (DES) ou a máquina virtual como consequência de execução de um thread.

## <a name="see-also"></a>Consulte também
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)