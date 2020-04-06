---
title: Visão geral do serviço de idioma legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707353"
---
# <a name="legacy-language-service-overview"></a>Visão geral do serviço de linguagem herdado
Um serviço de idiomafornece suporte ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor que permite implementar certos recursos. As classes de serviço de idiomas Managed Package Framework (MPF) fornecem suporte total para recursos usados com freqüência e suporte parcial para outros recursos.

## <a name="fully-supported-features-in-the-mpf"></a>Recursos totalmente suportados no MPF
 As classes de serviço de idiomas do MPF suportam os seguintes recursos:

- Realce de sintaxe

- Estrutura de tópicos

- Blocos de código comentando

- Correspondência de chaves

- Snippets de código

- Propriedades de documentos personalizados

- Informações sobre parâmetros do IntelliSense

- Informações rápidas do IntelliSense

- Conclusão do membro intelliSense

- Conclusão de palavra intelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Recursos parcialmente apoiados no MPF
 O MPF fornece apenas suporte parcial para os seguintes recursos. Isso significa que você deve implementar os métodos que são chamados pelo MPF.

- Código reformatador. Você fornece o código que implementa a reformatação.

- Validando pontos de interrupção identificando intervalos de código válidos. Você fornece o código que identifica os intervalos de código.

- Suporte à janela **Debugger Autos** para exibir variáveis. Você fornece o código que determina o que mostrar na janela.

- Suporte à **barra de navegação** para navegação rápida entre tipos e membros. Você implementa e retorna uma classe de ajudantes que preencha as listas nas caixas de combinação **da barra de navegação.**

## <a name="implementation"></a>Implementação
 Você deve concluir várias etapas para implementar o próprio serviço de idiomas e os recursos de serviço de idioma que você deseja suportar para o seu idioma. Essas etapas são discutidas nos seguintes tópicos:

- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Correspondência de chaves em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Comentando o código em um serviço de linguagem herdado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Reformatando o código em um serviço de linguagem herdado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Propriedades de documento personalizadas em um serviço de linguagem herdado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Suporte para snippets de código em um serviço de linguagem herdado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Suporte para a barra de navegação em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Preenchimento de palavra em um serviço de linguagem herdado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Preenchimento de membro em um serviço de linguagem herdado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Informações rápidas em um serviço de linguagem herdado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Suporte para a janela de automáticos em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Validando pontos de interrupção em um serviço de linguagem herdado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Confira também
- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Extensibilidade do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-extensibility.md)
