---
title: Registros de ativação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 125acbbca2723a9fbd9f41932782a62e966bcdd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864308"
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