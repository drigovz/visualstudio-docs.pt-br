---
title: Detalhes da configuração do controle de fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705288"
---
# <a name="source-control-configuration-details"></a>Detalhes de configuração de controle do código-fonte
Para implementar o controle de origem, você precisa configurar adequadamente seu sistema de projeto ou editor para fazer o seguinte:

- Peço permissão para transição para estado alterado

- Solicitar permissão para salvar um arquivo

- Solicitar permissão para adicionar, remover ou renomear arquivos no projeto

## <a name="request-permission-to-transition-to-changed-state"></a>Permissão de solicitação para transição para estado alterado
 Um projeto ou editor deve solicitar permissão para fazer <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>a transição para o estado alterado (sujo) ligando . Cada editor que <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> deve ligar e receber aprovação para `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>alterar o documento do ambiente antes de retornar para . Um projeto é essencialmente um editor para um arquivo de projeto e, como resultado, tem a mesma responsabilidade de implementar o rastreamento de estado alterado para o arquivo do projeto como um editor de texto faz para seus arquivos. O ambiente lida com o estado alterado da solução, mas você deve lidar com o estado alterado de qualquer objeto que a solução faz referência, mas não armazena, como um arquivo de projeto ou seus itens. Em geral, se o seu projeto ou editor é responsável pelo gerenciamento da persistência de um item, então ele é responsável pela implementação do rastreamento de estado alterado.

 Em resposta `IVsQueryEditQuerySave2::QueryEditFiles` à chamada, o ambiente pode fazer o seguinte:

- Rejeitar a chamada para alterar, nesse caso o editor ou projeto deve permanecer no estado inalterado (limpo).

- Indique que os dados do documento devem ser recarregados. Para um projeto, o ambiente recarregará os dados do projeto. Um editor deve recarregar os <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> dados do disco através de sua implementação. Em ambos os casos, o contexto no projeto ou editor pode mudar quando os dados são recarregados.

  É uma tarefa complexa e difícil `IVsQueryEditQuerySave2::QueryEditFiles` para readequar chamadas apropriadas para uma base de código existente. Como resultado, essas chamadas devem ser integradas durante a criação do projeto ou editor.

## <a name="request-permission-to-save-a-file"></a>Permissão de solicitação para salvar um arquivo
 Antes que um projeto ou editor salve <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>um arquivo, ele deve ligar ou . Para arquivos de projeto, essas chamadas são preenchidas automaticamente pela solução, que sabe quando salvar um arquivo de projeto. Os editores são responsáveis por fazer `IVsPersistDocData2` essas chamadas, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>a menos que a implementação do editor use a função auxiliar . Se o seu `IVsPersistDocData2` editor implementar desta forma, então a chamada para `IVsQueryEditQuerySave2::QuerySaveFile` ou `IVsQueryEditQuerySave2::QuerySaveFiles` é feita para você.

> [!NOTE]
> Sempre faça essas chamadas preventivamente — ou seja, em um momento em que seu editor possa receber um cancelamento.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Solicitar permissão para adicionar, remover ou renomear arquivos no projeto
 Antes que um projeto possa adicionar, renomear ou remover um `IVsTrackProjectDocuments2::OnQuery*` arquivo ou diretório, ele deve chamar o método apropriado para solicitar permissão do ambiente. Se a permissão for concedida, o projeto deve `IVsTrackProjectDocuments2::OnAfter*` concluir a operação e, em seguida, chamar o método apropriado para notificar o ambiente de que a operação está concluída. O projeto deve chamar os <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos da interface para todos os arquivos (por exemplo, arquivos especiais) e não apenas os arquivos pai. Chamadas de arquivo são obrigatórias, mas as chamadas de diretório são opcionais. Se o seu projeto tiver informações sobre <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> o diretório, então ele deve chamar os métodos apropriados, mas se ele não tiver essas informações, então o ambiente inferirá as informações do diretório.

 O projeto não deve chamar `IVsTrackProjectDocuments2` os métodos de abrir ou fechar o projeto. Os ouvintes que desejam essas <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> informações na startup podem esperar pelo evento e iterar através da solução para encontrar as informações de que precisam. No desligamento, essas informações não são necessárias. `IVsTrackProjectDocuments2`é fornecido a <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>partir do .

 Para cada adição, renomear e remover `OnQuery*` a `OnAfter*` ação, há um método e um método. Ligue `OnQuery*` para o método para pedir permissão para adicionar, renomear ou remover o arquivo ou diretório. Ligue `OnAfter*` para o método depois que o arquivo ou diretório tiver sido adicionado, renomeado ou removido e o estado do projeto reflete o novo estado.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Suporte para controle do código-fonte](../../extensibility/internals/supporting-source-control.md)
