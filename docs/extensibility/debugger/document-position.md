---
title: Posição do documento | Microsoft Docs
description: Saiba como uma posição de documento na depuração do Visual Studio fornece uma abstração de uma posição em um arquivo de origem como conhecido pelo IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42f85d0d15c46cfdfc2b76130649976d15035d7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840711"
---
# <a name="document-position"></a>Posição do documento
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, uma *posição de documento*:

- Fornece uma abstração de uma posição em um arquivo de origem como conhecido pelo IDE. Para a maioria dos idiomas hoje, uma posição de documento pode ser considerada como uma posição em um arquivo de origem.

- Descreve uma posição em um documento de origem para um mecanismo de depuração.

- É implementado por uma interface [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>Consulte também
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Contexto do documento](../../extensibility/debugger/document-context.md)
- [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de provedor de símbolo](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)
