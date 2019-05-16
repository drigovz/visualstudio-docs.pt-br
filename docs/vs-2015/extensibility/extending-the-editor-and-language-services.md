---
title: Estender o Editor e os serviços de linguagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674776"
---
# <a name="extending-the-editor-and-language-services"></a>Estendendo o editor e os serviços de linguagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode adicionar recursos de serviço de linguagem (como o IntelliSense) para o seu próprio editor e estender a maioria dos recursos do editor de código do Visual Studio.  Para obter uma lista completa de como você pode estender, consulte [serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Usando o Managed Extensibility Framework (MEF) para estender a maioria dos recursos do editor. Por exemplo, se o recurso de editor que você deseja estender coloração de sintaxe, você pode escrever um MEF *parte do componente* que define as classificações para o qual você deseja cores diferentes e como eles devem ser tratados. O editor também dá suporte a várias extensões do mesmo recurso.  
  
 A camada de apresentação do editor baseia-se o Windows Presentation Framework (WPF). WPF fornece uma biblioteca de elementos gráficos para formatação de texto flexível e também fornece visualizações como gráficos e animações.  
  
 O SDK do Visual Studio fornece adaptadores conhecidos como *shims* para dar suporte a VSPackages que foram escritos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos que você atualize para a nova tecnologia para obter melhor desempenho e confiabilidade.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Introdução ao serviço de linguagem e às extensões do editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica como criar uma extensão do editor.|  
|[Dentro do Editor](../extensibility/inside-the-editor.md)|Descreve a estrutura geral do editor e lista alguns dos seus recursos.|  
|[Managed Extensibility Framework no editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica como usar o MEF Managed Extensibility Framework () com o editor.|  
|[Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)|Lista os pontos de extensão do editor. Pontos de extensão representam os recursos do editor que podem ser estendidos.|  
|[Passo a passo: criar um adorno de exibição, comandos e configurações (guias de coluna)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Percorre e explica a criação de um adorno de exibição que desenha linhas de gudie de coluna para ajudar a manter o código para uma determinada largura de exibição.  Também mostra lendo e gravando configurações, bem como declarar e implementar comandos que você pode invocar da janela de comando.|  
|[Importações do editor](../extensibility/editor-imports.md)|Lista os serviços que uma extensão pode ser importado.|  
|[Adaptando um código herdado para o editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica as diferentes maneiras de se adaptar (pré-Visual Studio 2010) para estender o editor de código herdado.|  
|[Migrar um serviço de linguagem herdado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica como migrar um serviço de linguagem de VSPackage com base.|  
|[Passo a passo: vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Mostra como vincular um tipo de conteúdo para uma extensão de nome de arquivo.|  
|[Passo a passo: criar um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md)|Mostra como adicionar um ícone para uma margem.|  
|[Passo a passo: realçar o texto](../extensibility/walkthrough-highlighting-text.md)|Mostra como usar *marcas* para realçar o texto.|  
|[Passo a passo: estrutura de tópicos](../extensibility/walkthrough-outlining.md)|Mostra como adicionar a estrutura de tópicos para tipos específicos de chaves.|  
|[Passo a passo: exibir chaves correspondentes](../extensibility/walkthrough-displaying-matching-braces.md)|Mostra como destacar chaves correspondentes.|  
|[Passo a passo: exibir dicas de ferramenta Informações Rápidas](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Mostra como exibir o pop-ups QuickInfo que descrevem os elementos de código como propriedades, métodos e eventos.|  
|[Passo a passo: exibir a ajuda da assinatura](../extensibility/walkthrough-displaying-signature-help.md)|Mostra como exibir o pop-ups que fornecem informações sobre o número e tipos de parâmetros em uma assinatura.|  
|[Passo a passo: exibir o preenchimento de declaração](../extensibility/walkthrough-displaying-statement-completion.md)|Mostra como implementar a conclusão da instrução.|  
|[Passo a passo: implementar snippets de código](../extensibility/walkthrough-implementing-code-snippets.md)|Mostra como implementar a expansão de trecho de código.|  
|[Passo a passo: exibir sugestões de lâmpada](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Mostra como exibir as lâmpadas para sugestões de código.|  
|[Passo a passo: usar um comando do shell com uma extensão do editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Mostra como associar um comando de menu em um VSPackage com um componente MEF.|  
|[Passo a passo: usar uma tecla de atalho com uma extensão do editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Mostra como associar um atalho de menu em um VSPackage com um componente MEF.|  
|[MEF (Managed Extensibility Framework)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Fornece informações sobre o MEF Managed Extensibility Framework ().|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Fornece informações sobre o Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Referência  
 Editor do Visual Studio inclui os seguintes namespaces.  
  
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
