---
title: Salvando um documento padrão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724091"
---
# <a name="saving-a-standard-document"></a>Salvando um documento padrão
O ambiente manipula os comandos salvar, salvar como e salvar todos. Quando um usuário seleciona **salvar**, **salvar como**ou **salvar tudo** no menu **arquivo** ou fecha a solução, resultando em um **salvamento de tudo**, o processo a seguir ocorre.

 ![Editor padrão](../../extensibility/internals/media/public.gif "Público") Salvar, salvar como e salvar todo o tratamento de comandos para um editor padrão

 Esse processo é detalhado nas seguintes etapas:

1. Quando os comandos **salvar** e **salvar como** são selecionados, o ambiente usa o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para determinar a janela do documento ativo e, portanto, quais itens devem ser salvos. Depois que a janela do documento ativo é conhecida, o ambiente localiza o ponteiro de hierarquia e o identificador de item (itemID) do documento na tabela de documentos em execução. Para obter mais informações, consulte [executando a tabela de documentos](../../extensibility/internals/running-document-table.md).

    Quando o comando **salvar tudo** estiver selecionado, o ambiente usará as informações na tabela documento em execução para compilar a lista de todos os itens a serem salvos.

2. Quando a solução recebe uma chamada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, ela itera no conjunto de itens selecionados (ou seja, as várias seleções expostas pelo serviço <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. Em cada item na seleção, a solução usa o ponteiro de hierarquia para chamar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> para determinar se o comando de menu **salvar** deve ser habilitado. Se um ou mais itens estiverem sujos, o comando **salvar** será habilitado. Se a hierarquia usar um editor padrão, a hierarquia delegará a consulta de status sujo para o editor chamando o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Em cada item selecionado que está sujo, a solução usa o ponteiro de hierarquia para chamar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> nas hierarquias apropriadas.

    É comum que a hierarquia use um editor padrão para editar o documento. Nesse caso, o objeto de dados do documento para esse editor deve dar suporte à interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>. Após receber a chamada do método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>, o projeto deve informar ao editor que o documento está sendo salvo chamando o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> no objeto de dados do documento. O editor pode permitir que o ambiente manipule a caixa de diálogo **salvar como** , chamando `Query Service` para a interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Isso retorna um ponteiro para a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. O editor deve então chamar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>, passando um ponteiro para a implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> do editor por meio do parâmetro `pPersistFile`. Em seguida, o ambiente executa a operação de salvamento e fornece a caixa de diálogo **salvar como** para o editor. O ambiente então chama de volta para o editor com <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Se o usuário estiver tentando salvar um documento sem título (ou seja, um documento não salvo anteriormente), um comando Salvar como será realmente executado.

6. Para o comando Salvar como, o ambiente exibe a caixa de diálogo Salvar como, solicitando ao usuário um nome de arquivo.

    Se o nome do arquivo tiver sido alterado, a hierarquia será responsável por atualizar as informações em cache do quadro do documento chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Se o comando **salvar como** mover o local do documento e a hierarquia for sensível ao local do documento, a hierarquia será responsável por entregar a propriedade da janela abrir documento para outra hierarquia. Por exemplo, isso ocorre se o projeto acompanhar se o arquivo é um arquivo interno ou externo (arquivo variado) em relação ao projeto. Use o procedimento a seguir para alterar a propriedade de um arquivo para o projeto de arquivos diversos.

## <a name="changing-file-ownership"></a>Alterando a propriedade do arquivo

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para alterar a propriedade do arquivo para o projeto de arquivos diversos

1. Serviço de consulta para a interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>.

     Um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> é retornado.

2. Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) para transferir o documento para a nova hierarquia. A hierarquia que executa o comando Salvar como chama esse método.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)