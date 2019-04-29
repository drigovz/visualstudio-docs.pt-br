---
title: 'Como: Abrir editores padrão | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f34a239628c3ed9e8bccaa8590cb22100d7d290f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862908"
---
# <a name="how-to-open-standard-editors"></a>Como: Abrir editores padrão
Quando você abre um editor padrão, deixar o IDE determinar um editor padrão para um tipo de arquivo designado, em vez de especificar um editor específico do projeto para o arquivo.

 Conclua o procedimento a seguir para implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método. Isso abrirá um arquivo de projeto em um editor padrão.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Para implementar o método OpenItem com um editor padrão

1. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) para determinar se o arquivo de objeto de dados de documento já está aberto.

2. Se o arquivo já estiver aberto, repavimentar o arquivo chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> método, especificando um valor de `IDO_ActivateIfOpen` para o `grfIDO` parâmetro.

     Se o arquivo está aberto e o documento pertencente a um projeto diferente que o projeto de chamada, o seu projeto receber um aviso de que o editor que está sendo aberto é de outro projeto. A janela de arquivo, em seguida, é exibida.

3. Se o documento não está aberto ou não na tabela de documento em execução, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método (`OSE_ChooseBestStdEditor`) para abrir um editor padrão para o arquivo.

     Quando você chama o método, o IDE executa as seguintes tarefas:

    1. O IDE examina os editores / {guidEditorType} / subchave de extensões no registro para determinar qual editor pode abrir o arquivo e tem a prioridade mais alta para fazer isso.

    2. Depois que o IDE determinou qual editor pode abrir o arquivo, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. A implementação do editor desse método retorna informações que é necessárias para o IDE chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> e os documentos abertos recentemente do site.

    3. Por fim, o IDE carrega o documento usando a interface de persistência usuais, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.

    4. Se o IDE anteriormente determinou que a hierarquia ou um item de hierarquia está disponível, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> método no projeto para obter um contexto de nível de projeto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> ponteiro passar de volta com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> chamada de método.

4. Retornar um <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> ponteiro para o IDE quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> em seu projeto se você quiser permitir que o contexto de get de editor do seu projeto.

     Executar esta etapa permite que os serviços adicionais de oferta do projeto no Editor.

     Se a exibição de documento ou o objeto de exibição de documento com êxito foi localizado em um quadro de janela, o objeto é inicializado com seus dados por meio da chamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Abrir e salvar itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)
- [Como: Editores abertos específicos do projeto](../extensibility/how-to-open-project-specific-editors.md)
- [Como: Abrir editores para documentos abertos](../extensibility/how-to-open-editors-for-open-documents.md)
- [Exibir arquivos usando o comando Abrir arquivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)