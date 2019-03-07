---
title: Salvando um documento personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 896d56dc3fd66cd3dd9e733e8ae528ab710dbd83
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619687"
---
# <a name="saving-a-custom-document"></a>Salvando um documento personalizado
Os identificadores de ambiente do **salve**, **Salvar como**, e **Salvar tudo** comandos. Quando um usuário clica **salvar**, **Salvar como**, **ou salvar tudo** sobre a **arquivo** menu ou fecha a solução, resultando em um Salvar tudo, o seguinte processo ocorre.

 ![Cliente Editor Save](../../extensibility/internals/media/private.gif "privada") salvar, salvar como e salvar tudo manipulação de comando para um editor personalizado

 Esse processo é detalhado nas etapas a seguir:

1.  Para o **salve** e **Salvar como** comandos, o ambiente usa o <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> de serviço para determinar a janela do documento ativo e, portanto, quais itens devem ser salvas. Depois que a janela de documento ativa é conhecida, o ambiente localiza o ponteiro de hierarquia e o identificador do item (itemID) para o documento na tabela de documento em execução. Para obter mais informações, consulte [tabela de documento em execução](../../extensibility/internals/running-document-table.md).

     Para o comando Salvar tudo, o ambiente usa as informações na tabela de documento em execução para compilar a lista de todos os itens para salvar.

2.  Quando a solução recebe um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chamada, ele itera no conjunto de itens selecionados (ou seja, as várias seleções expostas pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service).

3.  Em cada item na seleção, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar se o comando de menu Salvar deve ser habilitado. Se um ou mais itens estiverem sujos, o comando Save está habilitado. Se a hierarquia usa um editor padrão, em seguida, os delegados de hierarquia consultando sujos status para o editor chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.

4.  Em cada item selecionado está sujo, a solução usa o ponteiro de hierarquia para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método nas hierarquias apropriados.

     No caso de um editor personalizado, a comunicação entre o objeto de dados de documento e o projeto é privada. Assim, preocupações relacionadas à persistência especiais são tratadas entre esses dois objetos.

    > [!NOTE]
    >  Se você implementar sua própria persistência, certifique-se de chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> método para economizar tempo. Esse método verifica para ter certeza de que é seguro salvar o arquivo (por exemplo, o arquivo não é somente leitura).

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)