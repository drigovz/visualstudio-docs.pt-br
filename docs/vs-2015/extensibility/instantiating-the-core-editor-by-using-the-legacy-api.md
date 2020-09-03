---
title: Instanciar o editor principal usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203919"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Instanciar o Editor de núcleo usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor é responsável por funções de edição de texto, como inserção, exclusão, cópia e colagem. Ele combina essas funções com as fornecidas por serviços de linguagem, como coloração de texto, recuo e conclusão de instrução IntelliSense.  
  
 Você pode instanciar uma instância do editor principal de uma das três maneiras:  
  
- Crie explicitamente uma instância do editor principal em uma janela.  
  
- Fornecer uma fábrica de editor que retorna uma instância do editor principal  
  
- Abra um arquivo da hierarquia do projeto.  
  
  As seções a seguir discutem como usar a API herdada para criar uma instância do editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Abrindo explicitamente uma instância do editor principal  
 Ao obter explicitamente uma instância do editor principal:  
  
- Obtenha um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para manter o objeto de dados do documento sendo editado.  
  
- Crie uma representação orientada por linha do objeto de dados de documento criando uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface.  
  
- Defina <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> como o objeto de dados de documento para uma instância da implementação padrão da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interface, usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> método.  
  
   Hospede a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> instância em uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> método.  
  
  Neste ponto, a exibição da <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface fornece uma janela que contém uma instância do editor principal.  
  
  No entanto, essa não é uma instância muito útil, porque não tem teclas de atalho ou acesso a recursos avançados. Para obter acesso a teclas de atalho e recursos avançados:  
  
- Use o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método para associar um serviço de linguagem e o objeto de dados de documento que o editor usa.  
  
- Crie suas próprias teclas de atalho ou use o padrão do sistema definindo as <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Propriedades de exibição dos objetos. Para fazer isso, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> método com a <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> propriedade.  
  
   Para obter e usar as teclas de atalho não padrão, gere-as usando o arquivo. vsct. Para obter mais informações, consulte [tabela de comandos do Visual Studio (. Vsct) arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Como usar uma fábrica de editor para obter o editor principal  
 Ao implementar um editor de núcleo com uma fábrica de editor usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, siga todas as etapas descritas na seção anterior para hospedar explicitamente um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> usando um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto de dados de documento em um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto.  
  
 Para exibir o texto, obtenha uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto e chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para fornecer um serviço de idioma para o editor, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método dentro do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para obter as teclas de atalho padrão, diferentemente da seção anterior, use o contexto de comando retornado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método ao obter o editor de núcleo do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método retornar o mesmo GUID de comando que o editor de texto, a instância do editor principal obterá automaticamente as teclas de atalho padrão.  
  
 Para obter informações gerais, consulte [Walkthrough: Criando um editor principal e registrando um tipo de arquivo do editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Dentro do editor principal](../extensibility/inside-the-core-editor.md)   
 [Abrindo e salvando itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Passo a passo: Criar um editor principal e registrar um tipo de arquivo do editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
