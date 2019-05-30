---
title: Contexto de documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d15e53d29adc04a82274ebd456027d15b0e41703
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345709"
---
# <a name="document-context"></a>Contexto de documento
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um *contexto de documento*:

- Representa uma posição em um arquivo de origem. Para os idiomas em que o arquivo de origem não pode estar presente, um contexto de documento identifica uma posição em um documento gerado normalmente pelo ambiente de tempo de execução. Por exemplo, um mecanismo de script pode gerar um documento de script. Para obter mais informações, consulte [documentar posição](../../extensibility/debugger/document-position.md).

- Descreve uma posição em um documento de origem que corresponde a um contexto de código. O manipulador de símbolo mapeia um contexto de código ao contexto da documentação, usando as informações geradas por um compilador ou interpretador.

- É implementado por uma [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.

## <a name="see-also"></a>Consulte também
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de provedor de símbolos](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)