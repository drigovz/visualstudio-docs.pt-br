---
title: Extensibilidade do Serviço de Linguagem Legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707403"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilidade do serviço de linguagem herdado
Um serviço de idioma fornece suporte específico ao idioma para editar código-fonte no IDE.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova maneira de implementar um serviço de idiomas, consulte [Editor e Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

 Esta seção discute a estrutura e a implementação de um serviço de linguagem legado.

## <a name="in-this-section"></a>Nesta seção
- [Migrando um serviço de linguagem herdado](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Explica como atualizar um serviço de idiomas do Visual Studio 2008 para a versão mais recente.

- [Conceitos básicos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-essentials.md)

 Fornece informações importantes sobre como desenvolver serviços de linguagem para integrar uma linguagem de programação no Visual Studio.

- [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)

 Fornece links para tópicos que podem ajudá-lo a criar um serviço de idioma.

- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Fornece informações sobre o suporte ao destaque da sintaxe em um serviço de idiomas.

- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fornece informações sobre como usar o mpf (framework de pacote gerenciado) para implementar um serviço de idioma completo em código gerenciado.

- [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Descreve bibliotecas e ferramentas que permitem que você navegue por visualizações de árvores de símbolos no IDE.

## <a name="related-sections"></a>Seções relacionadas
- [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md)

 Fornece uma visão geral dos editores do Visual Studio.

- [Suporte do serviço de linguagem para depuração](../../extensibility/internals/language-service-support-for-debugging.md)

 Fornece informações sobre e um link para o Visual Studio Debugging SDK, que contém as informações necessárias para criar e personalizar componentes de depurador usados para depurar programas.
