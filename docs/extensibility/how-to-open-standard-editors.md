---
title: 'Como: Abrir Editores Padrão | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710786"
---
# <a name="how-to-open-standard-editors"></a>Como: Abrir editores padrão
Quando você abre um editor padrão, você permite que o IDE determine um editor padrão para um tipo de arquivo designado, em vez de especificar um editor específico do projeto para o arquivo.

 Complete o seguinte procedimento <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> para implementar o método. Isso abrirá um arquivo de projeto em um editor padrão.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Para implementar o método OpenItem com um editor padrão

1. Ligue <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock`( ) para determinar se o arquivo de objeto de dados do documento já está aberto.

2. Se o arquivo já estiver aberto, reapareça o arquivo chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> método, especificando um valor de `IDO_ActivateIfOpen` para o `grfIDO` parâmetro.

     Se o arquivo estiver aberto e o documento for de um projeto diferente do projeto de chamada, seu projeto recebe um aviso de que o editor que está sendo aberto é de outro projeto. A janela do arquivo é então em si.

3. Se o documento não estiver aberto ou não <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> na`OSE_ChooseBestStdEditor`tabela de documentos em execução, ligue para o método ( ) para abrir um editor padrão para o arquivo.

     Quando você chama o método, o IDE executa as seguintes tarefas:

    1. O IDE verifica a subchave Editores/{guidEditorType}/Extensões no registro para determinar qual editor pode abrir o arquivo e tem a maior prioridade para fazer isso.

    2. Depois que o IDE determinou qual editor pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>abrir o arquivo, o IDE chama . A implementação deste método pelo editor retorna as informações <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> necessárias para que o IDE ligue e site o documento recém-aberto.

    3. Finalmente, o IDE carrega o documento usando a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>usual de persistência, tais como .

    4. Se o IDE tiver determinado anteriormente que o item de hierarquia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> ou hierarquia está disponível, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> o método no projeto para obter um ponteiro de contexto de nível de projeto para passar de volta com a chamada do método.

4. Retorne <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> um ponteiro ao IDE quando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> o IDE chamar seu projeto se você quiser deixar o editor obter contexto do seu projeto.

     A realização dessa etapa permite que o projeto ofereça serviços adicionais ao editor.

     Se a exibição do documento ou objeto de exibição de documento foi configurado com sucesso em um quadro de janela, o objeto será inicializado com seus dados por chamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Abrir e salvar itens do projeto](../extensibility/internals/opening-and-saving-project-items.md)
- [Como: Abrir editores específicos de projetos](../extensibility/how-to-open-project-specific-editors.md)
- [Como: Abrir editores para documentos abertos](../extensibility/how-to-open-editors-for-open-documents.md)
- [Exibir arquivos usando o comando Abrir arquivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
