---
title: Informações rápidas em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705937"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informações rápidas em um serviço de linguagem herdado
O IntelliSense Quick Info mostra informações sobre um identificador na fonte quando o usuário coloca o caret no identificador e seleciona **Informações Rápidas** no menu **IntelliSense** ou mantém o cursor do mouse sobre o identificador. Isso faz com que uma dica da ferramenta apareça com informações sobre o identificador. Essas informações geralmente consistem no tipo de identificador. Quando o mecanismo de depuração estiver ativo, essas informações podem incluir o valor atual. O mecanismo de depuração fornece valores de expressão, enquanto o serviço de idioma lida apenas com identificadores.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte Passo a Passo: Exibindo dicas [de ferramentas do QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

 As classes de serviço de serviço de idioma sumário de pacote gerenciado (MPF) fornecem suporte total para exibir a dica da ferramenta Informações Rápidas do IntelliSense. Tudo o que você precisa fazer é fornecer o texto a ser exibido e ativar o recurso de informações rápidas.

 O texto a ser exibido é <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> obtido chamando o analisador <xref:Microsoft.VisualStudio.Package.ParseReason>de método com um valor de razão de análise de . Esta razão diz ao analisador para obter as informações do tipo (ou o que for apropriado para ser <xref:Microsoft.VisualStudio.Package.ParseRequest> exibido na ponta da ferramenta Informações Rápidas) para o identificador no local especificado no objeto. O <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto é o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que foi passado para o método.

 O analisador deve analisar tudo até <xref:Microsoft.VisualStudio.Package.ParseRequest> a posição no objeto para determinar os tipos de todos os identificadores. Em seguida, o analisador deve obter o identificador no local de solicitação de análise. Finalmente, o analisador deve passar os dados da <xref:Microsoft.VisualStudio.Package.AuthoringScope> ponta da ferramenta associados a esse <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> identificador para o objeto para que o objeto possa retornar o texto do método.

## <a name="enabling-the-quick-info-feature"></a>Ativando o recurso de informações rápidas
 Para habilitar o recurso Informações `CodeSense` rápidas, você deve definir os parâmetros e `QuickInfo` nomeados do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Esses atributos <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> definem as propriedades e as propriedades.

## <a name="implementing-the-quick-info-feature"></a>Implementando o recurso de informações rápidas
 A <xref:Microsoft.VisualStudio.Package.ViewFilter> classe lida com a operação Informações Rápidas do IntelliSense. Quando <xref:Microsoft.VisualStudio.Package.ViewFilter> a classe <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> recebe o comando, a classe chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método com a razão de <xref:Microsoft.VisualStudio.Package.ParseReason> análise e a localização do cuidador no momento em que o <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando foi enviado. O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analisador do método deve então analisar a fonte até o local dado e, em seguida, analisar o identificador no local dado para determinar o que exibir na ponta da ferramenta Informações Rápidas.

 A maioria dos analisadores faz uma análise inicial de todo o arquivo de origem e armazena os resultados em uma árvore de análise. A análise completa é realizada <xref:Microsoft.VisualStudio.Package.ParseReason> quando <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> é passada para o método. Outros tipos de análise podem então usar a árvore de análise para obter as informações desejadas.

 Por exemplo, o valor <xref:Microsoft.VisualStudio.Package.ParseReason> da razão de análise pode encontrar o identificador no local de origem e procurá-lo na árvore de análise para obter as informações do tipo. Essas informações de tipo <xref:Microsoft.VisualStudio.Package.AuthoringScope> são então passadas para <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> a classe, e são devolvidas pelo método.
