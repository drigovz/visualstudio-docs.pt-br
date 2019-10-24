---
title: Detalhes de configuração do controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a6c51dfe4ad9378af04da61dbd7e9011c4678f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723792"
---
# <a name="source-control-configuration-details"></a>Detalhes de configuração de controle do código-fonte
Para implementar o controle do código-fonte, você precisa configurar corretamente seu sistema ou editor de projeto para fazer o seguinte:

- Solicitar permissão para passar para o estado alterado

- Solicitar permissão para salvar um arquivo

- Solicitar permissão para adicionar, remover ou renomear arquivos no projeto

## <a name="request-permission-to-transition-to-changed-state"></a>Solicitar permissão para passar para o estado alterado
 Um projeto ou editor deve solicitar permissão para fazer a transição para o estado alterado (sujo) chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Cada editor que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e receber aprovação para alterar o documento do ambiente antes de retornar `True` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Um projeto é essencialmente um editor para um arquivo de projeto e, consequentemente, tem a mesma responsabilidade de implementar o acompanhamento de estado alterado para o arquivo de projeto como um editor de texto para seus arquivos. O ambiente manipula o estado alterado da solução, mas você deve manipular o estado alterado de qualquer objeto que a solução faz referência, mas não armazena, como um arquivo de projeto ou seus itens. Em geral, se seu projeto ou editor for responsável por gerenciar a persistência de um item, ele será responsável por implementar o acompanhamento de estado alterado.

 Em resposta à chamada de `IVsQueryEditQuerySave2::QueryEditFiles`, o ambiente pode fazer o seguinte:

- Rejeite a chamada para alterar, caso em que o editor ou projeto deve permanecer no estado inalterado (limpo).

- Indique que os dados do documento devem ser recarregados. Para um projeto, o ambiente recarregará os dados para o projeto. Um editor deve recarregar os dados do disco por meio de sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>. Em ambos os casos, o contexto no projeto ou editor pode ser alterado quando os dados são recarregados.

  É uma tarefa complexa e difícil de adaptar chamadas de `IVsQueryEditQuerySave2::QueryEditFiles` apropriadas para uma base de código existente. Como resultado, essas chamadas devem ser integradas durante a criação do projeto ou editor.

## <a name="request-permission-to-save-a-file"></a>Solicitar permissão para salvar um arquivo
 Antes que um projeto ou editor salve um arquivo, ele deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Para arquivos de projeto, essas chamadas são automaticamente concluídas pela solução, que sabe quando salvar um arquivo de projeto. Os editores são responsáveis por fazer essas chamadas, a menos que a implementação do editor de `IVsPersistDocData2` use a função auxiliar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Se o seu editor implementa `IVsPersistDocData2` dessa forma, a chamada para `IVsQueryEditQuerySave2::QuerySaveFile` ou `IVsQueryEditQuerySave2::QuerySaveFiles` é feita para você.

> [!NOTE]
> Sempre faça essas chamadas preemptivas, ou seja, por vez, quando o editor for capaz de receber um cancelamento.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Solicitar permissão para adicionar, remover ou renomear arquivos no projeto
 Antes que um projeto possa adicionar, renomear ou remover um arquivo ou diretório, ele deve chamar o método de `IVsTrackProjectDocuments2::OnQuery*` apropriado para solicitar permissão do ambiente. Se a permissão for concedida, o projeto deverá concluir a operação e, em seguida, chamar o método de `IVsTrackProjectDocuments2::OnAfter*` apropriado para notificar o ambiente de que a operação foi concluída. O projeto deve chamar os métodos da interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> para todos os arquivos (por exemplo, arquivos especiais) e não apenas os arquivos pai. As chamadas de arquivo são obrigatórias, mas as chamadas de diretório são opcionais. Se o seu projeto tiver informações de diretório, ele deverá chamar os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> apropriados, mas se não tiver essas informações, o ambiente inferirá as informações de diretório.

 O projeto não deve chamar os métodos de `IVsTrackProjectDocuments2` no projeto aberto ou fechado. Os ouvintes que desejam essas informações na inicialização podem aguardar o evento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> e iterar pela solução para encontrar as informações de que precisam. Ao desligar, essas informações não são necessárias. `IVsTrackProjectDocuments2` é fornecido pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Para cada ação adicionar, renomear e remover, há um método `OnQuery*` e um método `OnAfter*`. Chame o método `OnQuery*` para pedir permissão para adicionar, renomear ou remover o arquivo ou diretório. Chame o método `OnAfter*` depois que o arquivo ou diretório tiver sido adicionado, renomeado ou removido e o estado do projeto refletir o novo estado.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)