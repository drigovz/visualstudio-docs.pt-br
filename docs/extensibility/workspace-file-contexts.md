---
title: Contextos de arquivo de espaço de trabalho no Visual Studio | Microsoft Docs
description: Saiba mais sobre provedores de contexto de arquivo que implementam a interface IFileContextProvider para dar suporte a informações sobre espaços de trabalho de pasta aberta.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 271b05d78123136d47cb618e8ed38cea64b7beac
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877059"
---
# <a name="workspace-file-contexts"></a>Contextos de arquivo do espaço de trabalho

Todas as informações sobre espaços de trabalho de [pasta aberta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) são produzidas por "provedores de contexto de arquivo" que implementam a <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interface. Essas extensões podem procurar padrões em pastas ou arquivos, ler arquivos e makefiles do MSBuild, detectar dependências de pacote, etc. para acumular as informações necessárias para definir um contexto de arquivo. Um contexto de arquivo por si só não executa nenhuma ação, mas, em vez disso, fornece dados em que outra extensão pode agir.

Cada <xref:Microsoft.VisualStudio.Workspace.FileContext> um tem um `Guid` associado que identifica o tipo de dados que ele transporta. Um espaço de trabalho o usa `Guid` posteriormente para fazer a correspondência com as extensões que consomem os dados por meio da <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propriedade. Um provedor de contexto de arquivo é exportado com metadados que identificam de qual contexto `Guid` de arquivo ele pode produzir dados.

Uma vez definido, um contexto de arquivo pode ser associado a qualquer número de arquivos ou pastas no espaço de trabalho. Um determinado arquivo ou pasta pode ser associado a qualquer número de contextos de arquivo. É uma relação muitos-para-muitos.

Os cenários mais comuns para contextos de arquivo estão relacionados aos serviços de compilação, depuração e linguagem. Para obter mais informações, consulte os outros tópicos relacionados a esses cenários.

## <a name="file-context-lifecycle"></a>Ciclo de vida do contexto do arquivo

Os ciclos de vida de um `FileContext` são não determinísticos. A qualquer momento, um componente pode solicitar um conjunto de tipos de contexto de forma assíncrona. Os provedores que dão suporte a algum subconjunto dos tipos de contexto de solicitação serão consultados. A `IWorkspace` instância atua como o intermediário entre o consumidor e os provedores por meio do <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> método. Os consumidores podem solicitar um contexto e executar uma ação de curto prazo com base no contexto, enquanto outros podem solicitar um contexto e manter uma referência de vida longa.

As alterações podem acontecer em arquivos que fazem com que um contexto de arquivo se torne desatualizado. O provedor pode acionar um evento no `FileContext` para notificar os consumidores de atualizações. Por exemplo, se um contexto de compilação for fornecido para algum arquivo, mas uma alteração no disco invalida esse contexto, o produtor original poderá invocar o evento. Qualquer consumidor que ainda faz referência a isso `FileContext` pode então repetir a consulta para um novo `FileContext` .

>[!NOTE]
>Não há nenhum modelo de push para os consumidores. Os consumidores não serão notificados sobre o novo do provedor `FileContext` após sua solicitação.

## <a name="expensive-file-context-computations"></a>Computações de contexto de arquivo caro

Ler o conteúdo do arquivo do disco pode ser caro, especialmente quando um provedor precisa resolver a relação entre os arquivos. Por exemplo, um provedor pode ser consultado para um contexto de arquivo do arquivo de origem, mas o contexto do arquivo depende dos metadados de um arquivo de projeto. Analisar o arquivo de projeto ou avaliá-lo com o MSBuild é caro. Em vez disso, a extensão pode exportar um `IFileScanner` para criar `FileDataValue` dados durante a indexação do espaço de trabalho. Agora, quando solicitado para contextos de arquivo, o `IFileContextProvider` pode consultar rapidamente os dados indexados. Para obter mais informações sobre indexação, consulte o tópico [indexação de espaço de trabalho](workspace-indexing.md) .

>[!WARNING]
>Tenha cuidado com outras maneiras pelas quais você `FileContext` pode ser caro de computar. Algumas interações de interface do usuário são síncronas e contam com um alto volume de `FileContext` solicitações. Os exemplos incluem a abertura de uma guia do editor e a abertura de um menu de contexto **Gerenciador de soluções** . Essas ações fazem muitas solicitações de tipo de contexto de compilação.

## <a name="file-context-related-apis"></a>APIs relacionadas a contexto de arquivo

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contém dados e metadados.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> e <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> criar o contexto do arquivo.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exporta um provedor de contexto de arquivo.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> é usado para que os consumidores obtenham contextos de arquivo.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> define os tipos de contexto de compilação que a pasta aberta consumirá.

## <a name="file-context-actions"></a>Ações de contexto de arquivo

Embora a `FileContext` si seja apenas dados sobre alguns arquivos, uma <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> é uma maneira de expressar e agir sobre esses dados. `IFileContextAction` é flexível em seu uso. Dois de seus casos mais comuns são a criação e a depuração.

## <a name="reporting-progress"></a>Relatório de progresso

O <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> método é passado `IProgress<IFileContextActionProgressUpdate>` , mas o argumento não deve ser usado como esse tipo. `IFileContextActionProgressUpdate` é uma interface vazia e a invocação `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` pode gerar `NotImplementedException` . Em vez disso, o `IFileContextAction` deve converter o argumento para outro tipo, conforme necessário para o cenário.

Para obter informações sobre os tipos fornecidos pelo Visual Studio, consulte a documentação do respectivo cenário.

## <a name="file-context-action-related-apis"></a>APIs relacionadas a ações de contexto de arquivo

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> executa um comportamento com base em um `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> cria instâncias do `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> exporta o tipo `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Observação de arquivo

Um espaço de trabalho escuta as notificações de alteração de arquivo e fornece a <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Arquivos que correspondem à configuração "ExcludedItems" não produzirão eventos de notificação de arquivo. Um limite entre eventos é usado para simplificação de notificação e redução de duplicidades. Quando você precisar reagir a uma alteração de arquivo, deverá assinar esse serviço.

>[!TIP]
>O serviço de [indexação](workspace-indexing.md) do espaço de trabalho assina eventos de arquivo por padrão. As inclusões e modificações de arquivo farão com `IFileScanner` que os s de eventos relevantes sejam invocados para novos dados para esse arquivo. As exclusões de arquivo removerão os dados indexados. Você não precisa assinar seu `IFileScanner` para o serviço de Inspetor de arquivo.

## <a name="next-steps"></a>Próximas etapas

* [Indexação](workspace-indexing.md) -a indexação do espaço de trabalho coleta e mantém informações sobre o espaço de trabalho.
* [Espaços de trabalho](workspaces.md) -examine os conceitos do espaço de trabalho e o armazenamento de configurações.
