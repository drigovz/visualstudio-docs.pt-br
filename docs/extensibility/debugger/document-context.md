---
title: Contexto do documento | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738926"
---
# <a name="document-context"></a>Contexto do documento
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um *contexto de documento:*

- Representa uma posição em um arquivo de origem. Para idiomas onde o arquivo de origem pode não estar presente, um contexto de documento identifica uma posição em um documento normalmente gerado pelo ambiente de tempo de execução. Por exemplo, um mecanismo de scriptpode gerar um documento a partir do script. Para obter mais informações, consulte [A posição do documento](../../extensibility/debugger/document-position.md).

- Descreve uma posição em um documento fonte que corresponde a um contexto de código. O manipulador de símbolos mapeia um contexto de código para o contexto da documentação, usando informações geradas por um compilador ou intérprete.

- É implementado por uma interface [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Confira também
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces do provedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md)
