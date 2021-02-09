---
title: Contexto de código | Microsoft Docs
description: Saiba mais sobre o contexto de código na depuração do Visual Studio, que descreve uma posição no código que existe quando um programa é interrompido em um ponto de interrupção.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 685650e0e97c3f9851f051fdaa78f86252597ff8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930714"
---
# <a name="code-context"></a>Contexto de código
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um **contexto de código**:

- Fornece uma abstração de uma posição no código, como conhecido pelo mecanismo DE depuração (DE). Para a maioria das arquiteturas de tempo de execução hoje, um contexto de código pode ser considerado como um endereço no fluxo de instruções de um programa. Para linguagens não tradicionais, em que o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.

- Descreve a posição atual no fluxo de execução do programa que você está depurando.

- Existe somente quando um programa é interrompido em um ponto de interrupção.

- Tem um contexto de documento associado.

- É implementado por uma interface [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .

## <a name="see-also"></a>Confira também
- [Contexto do documento](../../extensibility/debugger/document-context.md)
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)
