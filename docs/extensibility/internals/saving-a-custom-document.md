---
title: Salvando um documento personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724081"
---
# <a name="saving-a-custom-document"></a>Salvando um documento personalizado
O ambiente manipula os comandos **salvar**, **salvar como**e **salvar todos** . Quando um usuário clica em **salvar**, **salvar como** **ou salvar tudo** no menu **arquivo** ou fecha a solução, resultando em um salvamento de tudo, o processo a seguir ocorre.

 ![Salvar do editor do cliente](../../extensibility/internals/media/private.gif "Particular") Salvar, salvar como e salvar todo o tratamento de comandos para um editor personalizado

 Esse processo é detalhado nas seguintes etapas:

1. Para os comandos **salvar** e **salvar como** , o ambiente usa o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para determinar a janela do documento ativo e, portanto, quais itens devem ser salvos. Depois que a janela do documento ativo é conhecida, o ambiente localiza o ponteiro de hierarquia e o identificador de item (itemID) do documento na tabela de documentos em execução. Para obter mais informações, consulte [executando a tabela de documentos](../../extensibility/internals/running-document-table.md).

     Para o comando salvar tudo, o ambiente usa as informações na tabela de documentos em execução para compilar a lista de todos os itens a serem salvos.

2. Quando a solução recebe uma chamada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, ela itera no conjunto de itens selecionados (ou seja, as várias seleções expostas pelo serviço <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. Em cada item na seleção, a solução usa o ponteiro de hierarquia para chamar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> para determinar se o comando de menu salvar deve ser habilitado. Se um ou mais itens estiverem sujos, o comando salvar será habilitado. Se a hierarquia usar um editor padrão, a hierarquia delegará a consulta de status sujo para o editor chamando o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Em cada item selecionado que está sujo, a solução usa o ponteiro de hierarquia para chamar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> nas hierarquias apropriadas.

     No caso de um editor personalizado, a comunicação entre o objeto de dados do documento e o projeto é particular. Portanto, qualquer preocupação especial de persistência é tratada entre esses dois objetos.

    > [!NOTE]
    > Se você implementar sua própria persistência, certifique-se de chamar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> para economizar tempo. Esse método verifica se é seguro salvar o arquivo (por exemplo, o arquivo não é somente leitura).

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)