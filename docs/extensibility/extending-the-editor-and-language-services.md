---
title: Ampliando o Editor e os Serviços de Idiomas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711709"
---
# <a name="extend-the-editor-and-language-services"></a>Estender o editor e os serviços de idiomas
Você pode adicionar recursos de serviço de idioma (como o IntelliSense) ao seu próprio editor e estender a maioria dos recursos do editor de códigos do Visual Studio.  Para obter uma lista completa do que você pode estender, consulte [pontos de extensão do serviço de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md).

 Você estende a maioria dos recursos do editor usando o Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada). Por exemplo, se o recurso de editor que você deseja estender é coloração de sintaxe, você pode escrever uma *parte do componente* MEF que define as classificações para as quais você deseja coloração diferente e como você quer que elas sejam tratadas. O editor também suporta várias extensões do mesmo recurso.

 A camada de apresentação do editor é baseada no Windows Presentation Framework (WPF). O WPF fornece uma biblioteca gráfica para formatação de texto flexível e também fornece visualizações, como gráficos e animações.

 O Visual Studio SDK fornece adaptadores conhecidos como *shims* para suportar VSPackages que foram escritos para versões anteriores. No entanto, se você tem um VSPackage existente, recomendamos que você atualize-o para a nova tecnologia para obter melhor desempenho e confiabilidade.

## <a name="related-topics"></a>Tópicos Relacionados

|Title|Descrição|
|-----------|-----------------|
|[Comece com o serviço de idiomas e extensões de editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica como criar uma extensão para o editor.|
|[Dentro do editor](../extensibility/inside-the-editor.md)|Descreve a estrutura geral do editor e lista algumas de suas características.|
|[Estrutura de extensibilidade gerenciada no editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica como usar o Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada) com o editor.|
|[Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)|Lista os pontos de extensão do editor. Os pontos de extensão representam os recursos do editor que podem ser estendidos.|
|[Passo a passo: Crie um adorno de exibição, comandos e configurações (guias de coluna)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Anda e explica a construção de um adorno de vista que desenha linhas-guia de coluna para ajudá-lo a manter o código a uma certa largura de exibição.  Também mostra configurações de leitura e escrita, bem como declarando e implementando comandos que você pode invocar a partir da Janela de Comando.|
|[Importações do editor](../extensibility/editor-imports.md)|Lista os serviços que uma extensão pode importar.|
|[Adapte o código legado ao editor](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Explica diferentes maneiras de adaptar o código legado (pré-Visual Studio 2010) para estender o editor.|
|[Migrar um serviço de idioma legado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica como migrar um serviço de idioma baseado em VSPackage.|
|[Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Mostra como vincular um tipo de conteúdo a uma extensão de nome de arquivo.|
|[Passo a passo: Crie um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md)|Mostra como adicionar um ícone a uma margem.|
|[Passo a passo: Texto de destaque](../extensibility/walkthrough-highlighting-text.md)|Mostra como usar *tags* para destacar texto.|
|[Passo a passo: Adicionar delineamento](../extensibility/walkthrough-outlining.md)|Mostra como adicionar delineamento para tipos específicos de aparelhos.|
|[Passo a passo: Exibir aparelhos correspondentes](../extensibility/walkthrough-displaying-matching-braces.md)|Mostra como destacar aparelhos correspondentes.|
|[Passo a passo: Exibir dicas de ferramentas do QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Mostra como exibir popups QuickInfo que descrevem elementos de código, como propriedades, métodos e eventos.|
|[Passo a passo: Ajuda na assinatura de exibição](../extensibility/walkthrough-displaying-signature-help.md)|Mostra como exibir popups que dão informações sobre o número e tipos de parâmetros em uma assinatura.|
|[Passo a passo: exibir preenchimento de declaração](../extensibility/walkthrough-displaying-statement-completion.md)|Mostra como implementar a conclusão da declaração.|
|[Passo a passo: Implementar trechos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Mostra como implementar a expansão de trechos de código.|
|[Passo a passo: Exibir sugestões de lâmpadas](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Mostra como exibir lâmpadas para sugestões de código.|
|[Passo a passo: Use um comando shell com uma extensão de editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Mostra como associar um comando de menu em um VSPackage com um componente MEF.|
|[Passo a passo: Use uma tecla de atalho com uma extensão de editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Mostra como associar um atalho de menu em um VSPackage com um componente MEF.|
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Fornece informações sobre o Quadro de Extensibilidade Gerenciada (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fornece informações sobre a Windows Presentation Foundation (WPF).|

## <a name="reference"></a>Referência
 O editor do Visual Studio inclui os seguintes namespaces.

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>
