---
title: Features2 do serviço de linguagem herdada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e7df7fc5c7532d2db45bc2b643a249d1e566c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88237900"
---
# <a name="legacy-language-service-features-2"></a>Recursos do serviço de linguagem herdada 2
Os tópicos a seguir listam alguns dos recursos de serviço herdado de linguagem que você pode fornecer.

 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente de implementar recursos de serviço de linguagem é usar extensões de MEF. Para saber mais sobre a nova maneira de implementar um serviço de linguagem, consulte [extensões de serviço de editor e linguagem](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Recomendamos que você comece a usar a nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de linguagem e permitirá que você aproveite os novos recursos do editor.

## <a name="in-this-section"></a>Nesta seção
- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Explica como implementar a cor da sintaxe.

- [Formatação automática em um serviço de linguagem herdado](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Explica como implementar a formatação automática.

- [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Explica como implementar a dica de ferramenta de informações de parâmetro do IntelliSense.

- [Preenchimento de declaração em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Explica como implementar a lista de instruções do IntelliSense e a lista de conclusão de membros.

- [Estrutura de tópicos e texto oculto em um serviço de linguagem herdado](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Explica como implementar a estrutura de tópicos ou texto oculto.

- [Como fornecer suporte estendido à estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica algumas das etapas na implementação do suporte a depurador.

## <a name="related-sections"></a>Seções relacionadas
