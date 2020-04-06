---
title: Conclusão do Word em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703170"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Preenchimento de palavra em um serviço de linguagem herdado
A conclusão da palavra preenche os caracteres faltantes em uma palavra parcialmente digitada. Se houver apenas uma conclusão possível, a palavra será concluída quando o caractere de conclusão for inserido. Se a palavra parcial corresponder a mais de uma possibilidade, uma lista de possíveis conclusões será exibida. Um caractere de conclusão pode ser qualquer personagem que não seja usado para identificadores.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte [Estendendo o Editor e os Serviços de Idiomas](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="implementation-steps"></a>Etapas de implementação

1. Quando o usuário seleciona **o Palavra Completa** no menu **IntelliSense,** o <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando é enviado para o serviço de idiomas.

2. A <xref:Microsoft.VisualStudio.Package.ViewFilter> classe pega o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> comando e chama o <xref:Microsoft.VisualStudio.Package.ParseReason>método com a razão de analisar de .

3. Em <xref:Microsoft.VisualStudio.Package.Source> seguida, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> a classe chama o método para obter a lista de possíveis <xref:Microsoft.VisualStudio.Package.CompletionSet> preenchimentos de palavras e, em seguida, exibe as palavras em uma lista de dicas de ferramenta usando a classe.

    Se houver apenas uma palavra <xref:Microsoft.VisualStudio.Package.Source> correspondente, a classe completa a palavra.

   Alternativamente, se o scanner <xref:Microsoft.VisualStudio.Package.TokenTriggers> retornar o valor do gatilho quando o <xref:Microsoft.VisualStudio.Package.Source> primeiro caractere de <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> um identificador for <xref:Microsoft.VisualStudio.Package.ParseReason>digitado, a classe detectará isso e chamará o método com a razão de análise de . Neste caso, o analisador deve detectar a presença de um caractere de seleção de membros e fornecer uma lista de membros.

## <a name="enabling-support-for-the-complete-word"></a>Ativando o suporte para a Palavra Completa
 Para habilitar o suporte `CodeSense` para conclusão de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> palavra, defina o parâmetro nomeado passado para o atributo do usuário associado ao pacote de idiomas. Isso define <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> a <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriedade na classe.

 Seu analisador deve retornar uma lista de declarações <xref:Microsoft.VisualStudio.Package.ParseReason>em resposta ao valor da razão de análise, para que a conclusão da palavra funcione.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementando o Word Completo no método ParseSource
 Para o preenchimento <xref:Microsoft.VisualStudio.Package.Source> de <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> palavras, <xref:Microsoft.VisualStudio.Package.AuthoringScope> a classe chama o método da classe para obter uma lista de possíveis correspondências de palavras. Você deve implementar a lista em uma <xref:Microsoft.VisualStudio.Package.Declarations> classe derivada da classe. Consulte <xref:Microsoft.VisualStudio.Package.Declarations> a classe para obter detalhes sobre os métodos que você deve implementar.

 Se a lista contiver apenas <xref:Microsoft.VisualStudio.Package.Source> uma única palavra, então a classe inserirá automaticamente essa palavra no lugar da palavra parcial. Se a lista contiver mais <xref:Microsoft.VisualStudio.Package.Source> de uma palavra, a classe apresentará uma lista de dicas de ferramentas a partir da qual o usuário pode selecionar a escolha apropriada.

 Também veja o exemplo <xref:Microsoft.VisualStudio.Package.Declarations> de uma implementação de classe na [conclusão de membros em um serviço de linguagem legado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
