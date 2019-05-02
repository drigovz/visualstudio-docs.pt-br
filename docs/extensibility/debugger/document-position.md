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
ms.openlocfilehash: fc9d1e793405b2eb83fe4f72980a71e44d1acbd1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926077"
---
# <a name="document-position"></a>Posição do documento
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um *documentar posição*:

- Fornece uma abstração de uma posição em um arquivo de origem como o IDE conhecido. Na maioria dos idiomas hoje em dia, uma posição de documento pode ser pensada como uma posição em um arquivo de origem.

- Descreve uma posição em um documento de origem para um mecanismo de depuração.

- É implementado por uma [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) interface.

## <a name="see-also"></a>Consulte também
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Contexto de documento](../../extensibility/debugger/document-context.md)
- [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de provedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)