---
title: Tem 2 serviço de linguagem herdado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7e0fa6a229929a34ed3654c3a4e03e02d1129b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333499"
---
# <a name="legacy-language-service-features"></a>Recursos do serviço de linguagem herdado
Os tópicos a seguir listam alguns dos recursos de serviço de linguagem herdada, que você pode fornecer.

 Serviços de linguagem herdado são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de linguagem, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> É recomendável que você comece a usar o novo editor de API mais rápido possível. Isso melhorará o desempenho do seu serviço de linguagem e permitem que você tirar proveito dos novos recursos do editor.

## <a name="in-this-section"></a>Nesta seção
- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Explica como implementar a coloração de sintaxe.

- [Formatação automática em um serviço de linguagem herdado](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Explica como implementar a formatação automática.

- [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Explica como implementar a dica de ferramenta de informações de parâmetro do IntelliSense.

- [Preenchimento de declaração em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Explica como implementar a lista de instrução do IntelliSense e a lista de preenchimento de membro.

- [Estruturar em tópicos e texto oculto em um serviço de linguagem herdado](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Explica como implementar texto oculto ou estrutura de tópicos.

- [Como: fornecer suporte expandido a estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica algumas das etapas na implementação de suporte do depurador...

## <a name="related-sections"></a>Seções relacionadas