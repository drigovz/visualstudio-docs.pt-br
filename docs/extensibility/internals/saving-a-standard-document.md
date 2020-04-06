---
title: Salvando um documento padrão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705544"
---
# <a name="saving-a-standard-document"></a>Salvando um documento padrão
O ambiente lida com os comandos Salvar, Salvar Como e Salvar Todos. Quando um usuário seleciona **Salvar**, **Salvar Como**ou **Salvar Tudo** no menu **Arquivo** ou fecha a solução, resultando em um **Save All,** o processo a seguir ocorre.

 ![Editor padrão](../../extensibility/internals/media/public.gif "Público") Salvar, salvar as e salvar todos os comandos para um editor padrão

 Este processo é detalhado nas seguintes etapas:

1. Quando os comandos **Salvar** e **Salvar como** <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> são selecionados, o ambiente usa o serviço para determinar a janela ativa do documento e, portanto, quais itens devem ser salvos. Uma vez que a janela ativa do documento é conhecida, o ambiente encontra o ponteiro de hierarquia e o identificador de item (itemID) para o documento na tabela de documentos em execução. Para obter mais informações, consulte [A tabela de documentos em execução](../../extensibility/internals/running-document-table.md).

    Quando o comando **Salvar tudo** é selecionado, o ambiente usa as informações na tabela de documentos em execução para compilar a lista de todos os itens a serem saqueados.

2. Quando a solução <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> recebe uma chamada, ela itera através do conjunto de itens selecionados <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> (ou seja, as múltiplas seleções expostas pelo serviço).

3. Em cada item da seleção, a solução <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> usa o ponteiro hierarquia para chamar o método para determinar se o comando **Salvar** menu deve ser ativado. Se um ou mais itens estiverem sujos, o comando **Salvar** está ativado. Se a hierarquia usar um editor padrão, a hierarquia delega consulta ndo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> status sujo para o editor, chamando o método.

4. Em cada item selecionado que está sujo, a solução <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> usa o ponteiro hierárquico para chamar o método nas hierarquias apropriadas.

    É comum que a hierarquia use um editor padrão para editar o documento. Neste caso, o objeto de dados do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> documento para esse editor deve suportar a interface. Ao receber <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> a chamada do método, o projeto deve informar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> ao editor que o documento está sendo salvo ligando para o método no objeto de dados do documento. O editor pode permitir que o ambiente manuseie <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> a caixa de diálogo **Salvar como,** chamando `Query Service` para a interface. Isso retorna um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ponteiro para a interface. O editor deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> então chamar o método, passando <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> um ponteiro `pPersistFile` para a implementação do editor por meio do parâmetro. Em seguida, o ambiente executa a operação Salvar e fornece a caixa de diálogo **Salvar como** para o editor. O ambiente então chama de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>volta para o editor com .

5. Se o usuário estiver tentando salvar um documento sem título (ou seja, um documento não salvo anteriormente), então um comando Save As será realmente executado.

6. Para o comando Salvar como, o ambiente exibe a caixa de diálogo Salvar como, solicitando ao usuário um nome de arquivo.

    Se o nome do arquivo tiver sido alterado, a hierarquia será responsável por <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>atualizar as informações armazenadas em cache do quadro de documentos ligando para (VSFPROPID_MkDocument).

   Se o comando **Salvar como** mover a localização do documento e a hierarquia for sensível à localização do documento, a hierarquia será responsável por entregar a propriedade da janela de documento aberta para outra hierarquia. Por exemplo, isso ocorre se o projeto for rastreado se o arquivo é um arquivo interno ou externo (Arquivo Diverso) em relação ao projeto. Use o procedimento a seguir para alterar a propriedade de um arquivo para o projeto Arquivos Diversos.

## <a name="changing-file-ownership"></a>Alterando a propriedade do arquivo

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para alterar a propriedade do arquivo para o projeto Arquivos Diversos

1. Serviço de consulta <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> para interface.

     Um ponteiro <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> para é devolvido.

2. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> o`pszMkDocumentNew` `punkWindowFrame`método () para transferir o documento para a nova hierarquia. A hierarquia que executa o comando Salvar como chama este método.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)
