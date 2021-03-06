---
title: Quadros de pilhas | Microsoft Docs
description: Este artigo descreve a definição e a função de um quadro de pilha na arquitetura do depurador no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97adb5d453e147c45ae1f268a20a2d3091286508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960722"
---
# <a name="stack-frames"></a>Quadros de pilha
Na arquitetura do depurador, um registro de *ativação*:

- É uma abstração de uma pilha que fornece o contexto de execução de um thread. Um thread sempre é executado dentro de uma função. Um registro de ativação contém as variáveis locais da função e os argumentos a ela. Para depurar com o Visual Studio, a linguagem ou o ambiente que está sendo depurado deve dar suporte a quadros de pilha.

- Pode identificar e descrever a si mesmo e pode retornar o thread associado. Um quadro de pilha também pode retornar o contexto de código que representa o ponteiro de instrução atual e os contextos de avaliação de documentação e expressão associados.

- Tem propriedades que descrevem o nome, o tipo e o valor de variáveis e argumentos locais, e que aparecem em várias janelas de depuração do IDE.

- É representado por uma interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , normalmente criada por um mecanismo de depuração (de) ou máquina virtual como consequência da execução de um thread.

## <a name="see-also"></a>Consulte também
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
