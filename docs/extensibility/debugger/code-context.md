---
title: Contexto de código | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739155"
---
# <a name="code-context"></a>Contexto de código
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um **contexto de código:**

- Fornece uma abstração de uma posição em código conhecida pelo motor de depuração (DE). Para a maioria das arquiteturas de tempo de execução hoje, um contexto de código pode ser pensado como um endereço no fluxo de instruções de um programa. Para línguas não tradicionais, onde o código pode não ser representado por instruções, um contexto de código pode ser representado por alguns outros meios.

- Descreve a posição atual no fluxo de execução do programa que você está depurando.

- Existe apenas quando um programa parou em um ponto de ruptura.

- Tem um contexto de documento associado.

- É implementado por uma interface [IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>Confira também
- [Contexto do documento](../../extensibility/debugger/document-context.md)
- [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md)
