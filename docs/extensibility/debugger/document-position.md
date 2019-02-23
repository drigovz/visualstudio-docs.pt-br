---
title: Posição de documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f025ca2d73e98f8191969510f866cb7eb1d0eea
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695942"
---
# <a name="document-position"></a>Posição do documento
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um *documentar posição*:

-   Fornece uma abstração de uma posição em um arquivo de origem como o IDE conhecido. Na maioria dos idiomas hoje em dia, uma posição de documento pode ser pensada como uma posição em um arquivo de origem.

-   Descreve uma posição em um documento de origem para um mecanismo de depuração.

-   É implementado por uma [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) interface.

## <a name="see-also"></a>Consulte também
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Contexto de documento](../../extensibility/debugger/document-context.md)
- [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de provedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)