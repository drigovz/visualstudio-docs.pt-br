---
title: Recursos do serviço de idioma legado1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707393"
---
# <a name="legacy-language-service-features"></a>Recursos do serviço de linguagem herdado
Um serviço de idioma de framework de pacote [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerenciado (MPF) pode suportar um ou mais recursos, como destaque de sintaxe, IntelliSense e validação de breakpoint. Cada recurso pode ser implementado independente dos outros, mas todos requerem um analisador e um scanner, exceto para o destaque da sintaxe, que requer apenas um scanner.

## <a name="in-this-section"></a>Nesta seção
- [Correspondência de chaves em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar a correspondência de pares de idiomas, também conhecido como correspondência de chaves.

- [Comentando o código em um serviço de linguagem herdado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar comentários e não comentários de código selecionado.

- [Propriedades de documento personalizadas em um serviço de linguagem herdado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar propriedades de documentos que estão incorporadas em um arquivo de origem.

- [Estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Descreve o que é necessário para apoiar o delineamento através da implementação de regiões ocultas.

- [Reformatando o código em um serviço de linguagem herdado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Descreve o que é necessário para apoiar o código reformatizador.

- [Suporte para snippets de código em um serviço de linguagem herdado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar trechos de código, que são segmentos de código que são inseridos e podem ser editados.

- [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Descreve o que é necessário para suportar a operação IntelliSense Parameter Info para exibir uma assinatura de método à medida que o método é digitado.

- [Informações rápidas em um serviço de linguagem herdado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar a operação Informações Rápidas do IntelliSense para exibir informações sobre um identificador.

- [Preenchimento de membro em um serviço de linguagem herdado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar a operação IntelliSense Member Completion para selecionar um membro de um namespace de uma lista.

- [Preenchimento de palavra em um serviço de linguagem herdado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar a operação IntelliSense Complete Word para completar palavras parcialmente digitadas.

- [Suporte para a janela de automáticos em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Descreve o que um serviço de idioma pode fazer para suportar a janela **Autos** enquanto você está depurando.

- [Suporte para a barra de navegação em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Descreve como usar a **barra de navegação** na parte superior da exibição do editor para fornecer navegação rápida a qualquer tipo ou membro no arquivo mostrado nessa exibição..

- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Descreve o que é necessário para suportar o destaque da sintaxe do código fonte.

- [Validando pontos de interrupção em um serviço de linguagem herdado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Descreve o que um serviço de idioma pode fazer para suportar a validação de pontos de interrupção fora de um depurador.

## <a name="related-sections"></a>Seções relacionadas
- [Analisador e scanner do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Descreve o analisador e o scanner necessários para implementar todos os recursos de um serviço de idioma que usa a estrutura de pacote gerenciada.

- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Descreve o que é necessário para implementar um serviço de idioma usando o MPF.

- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Descreve as etapas necessárias para registrar um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]serviço de idioma baseado no MPF com .

- [Usando o IntelliSense](../../ide/using-intellisense.md)

 Explica como o IntelliSense facilita o acesso das referências de idiomas.

- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fornece informações sobre como usar o mpf (framework de pacote gerenciado) para implementar um serviço de idioma completo em código gerenciado.
