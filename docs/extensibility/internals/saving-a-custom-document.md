---
title: Salvando um documento personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705611"
---
# <a name="saving-a-custom-document"></a>Salvando um documento personalizado
O ambiente lida com os comandos **Salvar,** **Salvar Como**e **Salvar Todos.** Quando um usuário **clica em Salvar**, Salvar **Como**, ou **Salvar tudo** no menu **Arquivo** ou fecha a solução, resultando em um Save All, o processo seguinte ocorre.

 ![Salvar editor de clientes](../../extensibility/internals/media/private.gif "Privado") Salvar, salvar as e salvar todos os comandos para um editor personalizado

 Este processo é detalhado nas seguintes etapas:

1. Para os comandos **Salvar** e Salvar <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> **como,** o ambiente usa o serviço para determinar a janela ativa do documento e, portanto, quais itens devem ser salvos. Uma vez que a janela ativa do documento é conhecida, o ambiente encontra o ponteiro de hierarquia e o identificador de item (itemID) para o documento na tabela de documentos em execução. Para obter mais informações, consulte [A tabela de documentos em execução](../../extensibility/internals/running-document-table.md).

     Para o comando Salvar todos, o ambiente usa as informações na tabela de documentos em execução para compilar a lista de todos os itens a serem saqueados.

2. Quando a solução <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> recebe uma chamada, ela itera através do conjunto de itens selecionados <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> (ou seja, as múltiplas seleções expostas pelo serviço).

3. Em cada item da seleção, a solução <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> usa o ponteiro hierarquia para chamar o método para determinar se o comando Salvar menu deve ser ativado. Se um ou mais itens estiverem sujos, o comando Salvar está ativado. Se a hierarquia usar um editor padrão, a hierarquia delega consulta ndo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> status sujo para o editor, chamando o método.

4. Em cada item selecionado que está sujo, a solução <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> usa o ponteiro hierárquico para chamar o método nas hierarquias apropriadas.

     No caso de um editor personalizado, a comunicação entre o objeto de dados do documento e o projeto é privada. Assim, quaisquer preocupações especiais de persistência são tratadas entre esses dois objetos.

    > [!NOTE]
    > Se você implementar sua própria persistência, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> certifique-se de chamar o método para economizar tempo. Este método verifica se é seguro salvar o arquivo (por exemplo, o arquivo não é somente leitura).

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)
