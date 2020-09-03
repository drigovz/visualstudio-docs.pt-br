---
title: Contexto de documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738926"
---
# <a name="document-context"></a>Contexto do documento
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um *contexto de documento*:

- Representa uma posição em um arquivo de origem. Para idiomas em que o arquivo de origem pode não estar presente, um contexto de documento identifica uma posição em um documento normalmente gerada pelo ambiente de tempo de execução. Por exemplo, um mecanismo de script pode gerar um documento a partir do script. Para obter mais informações, consulte [posição do documento](../../extensibility/debugger/document-position.md).

- Descreve uma posição em um documento de origem que corresponde a um contexto de código. O manipulador de símbolos mapeia um contexto de código para o contexto de documentação, usando informações geradas por um compilador ou intérprete.

- É implementado por uma interface [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="see-also"></a>Confira também
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de provedor de símbolo](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)
