---
title: Contexto de código | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11554be1411e63c97c8afde7cc3a819486e862ac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351321"
---
# <a name="code-context"></a>Contexto de código
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um **contexto de código**:

- Fornece uma abstração de uma posição no código como conhecidos para o mecanismo de depuração (DES). Para a maioria das arquiteturas de tempo de execução atualmente, um contexto de código pode ser pensado como um endereço no fluxo de instruções de um programa. Para idiomas não tradicionais, onde o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.

- Descreve a posição atual no fluxo de execução do programa que você está depurando.

- Existe apenas quando um programa foi interrompido no ponto de interrupção.

- Tem um contexto de documento associado.

- É implementado por uma [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interface.

## <a name="see-also"></a>Consulte também
- [Contexto de documento](../../extensibility/debugger/document-context.md)
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)