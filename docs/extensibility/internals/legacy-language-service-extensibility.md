---
title: Extensibilidade do serviço de linguagem herdado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14bee804d532138ddf5c9b63039f4bfb8abbe02c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344840"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilidade do serviço de linguagem herdado
Um serviço de linguagem fornece suporte de idioma específico para a edição de código-fonte no IDE.

 Serviços de linguagem herdado são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de linguagem, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).

 Esta seção discute a estrutura e a implementação de um serviço de linguagem herdada.

## <a name="in-this-section"></a>Nesta seção
- [Migrar um serviço de linguagem herdado](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Explica como atualizar um serviço de linguagem do Visual Studio 2008 para a versão mais recente.

- [Fundamentos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-essentials.md)

 Fornece informações importantes sobre como desenvolver serviços de linguagem para integrar uma linguagem de programação no Visual Studio.

- [Desenvolver um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)

 Fornece links para tópicos que podem ajudar você a criar um serviço de linguagem.

- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Fornece informações sobre o suporte a realce de sintaxe em um serviço de linguagem.

- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fornece informações sobre como usar a estrutura de pacote gerenciado (MPF) para implementar um serviço de linguagem completa no código gerenciado.

- [Suporte a ferramentas de navegação por símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Descreve as bibliotecas e ferramentas que permitem que você navegue os modos de exibição de árvore de símbolos no IDE.

## <a name="related-sections"></a>Seções relacionadas
- [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md)

 Fornece uma visão geral dos editores do Visual Studio.

- [Suporte do serviço de linguagem para depuração](../../extensibility/internals/language-service-support-for-debugging.md)

 Fornece informações sobre como e um link para o SDK do Visual Studio de depuração, que contém as informações necessárias para criar e personalizar componentes do depurador usados para depurar programas.