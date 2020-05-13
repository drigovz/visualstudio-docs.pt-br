---
title: Quadros de pilha | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712836"
---
# <a name="stack-frames"></a>Quadros de pilha
Na arquitetura dedepurador, um *quadro de pilha:*

- É uma abstração de uma pilha que fornece o contexto de execução de um segmento. Um segmento sempre é executado dentro de uma função. Um quadro de pilha contém as variáveis locais da função e os argumentos para ela. Para depurar com o Visual Studio, o idioma ou ambiente que está sendo depurado deve suportar quadros de pilha.

- Pode identificar e descrever a si mesmo, e pode retornar o segmento associado. Um quadro de pilha também pode retornar o contexto de código que representa o ponteiro de instrução atual e os contextos de documentação e avaliação de expressão associados.

- Tem propriedades que descrevem o nome, o tipo e o valor das variáveis e argumentos locais, e que aparecem em várias janelas de depuração do IDE.

- É representado por uma interface [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) normalmente criada por um mecanismo de depuração (DE) ou máquina virtual como conseqüência da execução de um thread.

## <a name="see-also"></a>Confira também
- [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuração](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
