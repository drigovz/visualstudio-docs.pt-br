---
title: Fábricas de editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197759"
---
# <a name="editor-factories"></a>Fábricas de editores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma fábrica de editor cria objetos de editor e os coloca em um quadro de janela, conhecido como exibição física. Ele cria os dados do documento e os objetos de exibição de documento que são necessários para criar editores e designers. Uma fábrica de editor é necessária para criar o editor de núcleo do Visual Studio e qualquer editor padrão. Um editor personalizado também pode ser criado opcionalmente com uma fábrica de editor.  
  
 Você cria uma fábrica de editor implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. O exemplo a seguir ilustra como implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> para criar uma fábrica de editor:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Um editor é carregado na primeira vez que você abre um tipo de arquivo manipulado por esse editor. Você pode optar por abrir um editor específico ou o editor padrão. Se você selecionar o editor padrão, o ambiente de desenvolvimento integrado (IDE) determinará o editor correto para abrir e, em seguida, o abrirá. Para obter mais informações, consulte [determinando qual editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrando fábricas do editor  
 Antes de usar um editor que você criou, primeiro você deve registrar informações sobre ele, incluindo as extensões de arquivo que ele pode manipular.  
  
 Se seu VSPackage for escrito em código gerenciado, você poderá usar o método MPF (Managed Package Framework) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para registrar a fábrica do editor depois que o VSPackage for carregado. Se seu VSPackage for escrito em código não gerenciado, você deverá registrar a fábrica do editor usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> serviço.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrando uma fábrica de editor usando código gerenciado  
 Você deve registrar a fábrica do editor no método do seu VSPackage `Initialize` . Primeira chamada `base.Initialize` e, em seguida, chamar <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para cada fábrica do editor  
  
 No código gerenciado, não é necessário cancelar o registro de uma fábrica do editor, pois o VSPackage tratará disso para você. Além disso, se a fábrica do editor implementar <xref:System.IDisposable> , ela será descartada automaticamente quando tiver seu registro cancelado.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrando uma fábrica de editor usando código não gerenciado  
 Na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementação do pacote do editor, use o `QueryService` método para chamar `SVsRegisterEditors` . Fazer isso retorna um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método passando a implementação da <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. Você deve mplementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> em uma classe separada.  
  
## <a name="the-editor-factory-registration-process"></a>O processo de registro de fábrica do editor  
 O processo a seguir ocorre quando o Visual Studio carrega seu editor usando a fábrica do editor:  
  
1. O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistema de projeto chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Esse método retorna a fábrica do editor. O Visual Studio atrasa o carregamento do pacote do editor, no entanto, até que um sistema de projeto realmente precise do editor.  
  
3. Quando um sistema de projeto precisa do editor, o Visual Studio chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , um método especializado que retorna o modo de exibição de documento e os objetos de dados do documento.  
  
4. Se chamadas pelo Visual Studio para sua fábrica de editor usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> retornar um objeto de dados de documento e um objeto de exibição de documento, o Visual Studio criará a janela de documento, colocará o objeto de exibição de documento nela e fará uma entrada na tabela de documentos em execução (Rdt) para o objeto de dados do documento.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabela de documento em execução](../extensibility/internals/running-document-table.md)
