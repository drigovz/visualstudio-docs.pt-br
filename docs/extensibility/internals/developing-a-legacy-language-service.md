---
title: Desenvolvendo um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708663"
---
# <a name="develop-a-legacy-language-service"></a>Desenvolva um serviço de linguagem legado
Esta seção se conecta a tópicos que ajudam você a criar um serviço de idioma legado.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova maneira de implementar um serviço de idiomas, consulte [Editor e extensões de serviços de idiomas](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="in-this-section"></a>Nesta seção
- [Modelo de um serviço de linguagem legado](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Fornece um modelo de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] serviço de linguagem mínimo para o editor principal. Você pode usar este modelo como um guia para criar seu próprio serviço de idiomas.

- [Interfaces de serviço de idioma legado](../../extensibility/internals/legacy-language-service-interfaces.md)

 Discute os objetos necessários para implementar um serviço de idioma e fornece uma lista de objetos adicionais que você pode usar para fornecer destaque de sintaxe, dados do método e outros recursos.

- [Interceptar comandos de serviço de linguagem legados](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Descreve como inserir um filtro de comando no serviço de idioma para interceptar comandos que a exibição de texto manteria de outra forma.

- [Registre um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Fornece informações sobre como registrar seu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]serviço de idioma usando .

- [Suporte a serviços de idiomas para depuração](../../extensibility/internals/language-service-support-for-debugging.md)

 Descreve como um serviço de idioma pode fornecer recursos para oferecer suporte a um depurador.

- [Checklist: Crie um serviço de idioma legado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Fornece instruções passo-a-passo para criar e integrar um serviço de idioma para o editor principal.

## <a name="related-sections"></a>Seções relacionadas
- [Colorir sintaxe em um serviço de linguagem legado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Discute como implementar o destaque de sintaxe no seu serviço de idiomas.

- [Conclusão da declaração em um serviço de idioma legado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Discute a conclusão da declaração, o processo pelo qual um serviço de idioma ajuda os usuários a terminar uma palavra-chave ou elemento de idioma que eles começaram a digitar.

- [Informações de parâmetros em um serviço de linguagem legado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Descreve como fornecer dicas de método para funções e métodos sobrecarregados.

- [Como: Fornecer suporte a texto oculto em um serviço de idioma legado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Explica o propósito de uma região de texto oculto e fornece instruções sobre como implementar uma região de texto oculto.

- [Como: Fornecer suporte de delineamento expandido em um serviço de idioma legado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica as duas opções que estendem o suporte delineamento para o seu idioma além de suportar o comando *'Colapso para Definições'.*
