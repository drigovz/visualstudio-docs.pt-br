---
title: Contextos de arquivo do espaço de trabalho no Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 93690eab989cee62d756a774675bf1d46da017fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826858"
---
# <a name="workspace-file-contexts"></a>Contextos de arquivo do espaço de trabalho

Todas as percepções [Abrir pasta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) espaços de trabalho são produzidos por "contexto provedores de arquivos" que implementam o <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interface. Essas extensões podem procurar por padrões nas pastas ou arquivos, leia arquivos do MSBuild e makefiles, detectam as dependências do pacote, etc. para acumular os insights que eles precisam para definir um contexto de arquivo. Um contexto de arquivo por si só não executa qualquer ação, mas em vez disso, fornece dados de outra extensão, em seguida, pode agir em.

Cada <xref:Microsoft.VisualStudio.Workspace.FileContext> tem um `Guid` associados a ela que identifica o tipo de dados ele carrega. Um espaço de trabalho usa esse `Guid` mais tarde para ter uma correspondência com extensões que consomem os dados por meio de <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propriedade. Um provedor de contexto do arquivo é exportado com metadados que identifica qual contexto de arquivo `Guid`s que ele pode produzir dados para.

Depois de definido, um contexto de arquivo pode ser associado com qualquer número de arquivos ou pastas no espaço de trabalho. Um determinado arquivo ou pasta pode estar associada com qualquer número de contextos de arquivo. É uma relação muitos-para-muitos.

Os cenários mais comuns para contextos de arquivo estão relacionados à compilação, depuração e serviços de linguagem. Para obter mais informações, consulte os outros tópicos relacionados a esses cenários.

## <a name="file-context-lifecycle"></a>Ciclo de vida do contexto de arquivo

Os ciclos de vida para um `FileContext` são não determinísticas. A qualquer momento, um componente de forma assíncrona pode solicitar para um conjunto de tipos de contexto. Provedores que dão suporte algum subconjunto dos tipos de contexto de solicitação serão consultados. O `IWorkspace` instância atua como intermediário entre o consumidor e provedores por meio de <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> método. Os consumidores podem solicitar um contexto e realizar alguma ação de curto prazo com base no contexto, enquanto outros podem solicitar um contexto e manter uma referência a vida útil longa. 

As alterações podem ocorrer para arquivos que fazem com que um contexto de arquivo para se tornar desatualizadas. O provedor pode acionar um evento no `FileContext` para notificar os consumidores de atualizações. Por exemplo, se um contexto de build é fornecido para algum arquivo, mas uma alteração em disco invalida nesse contexto, o produtor original pode invocar o evento. Consumidores ainda fazendo referência a ela `FileContext` , em seguida, pode repetir a consulta para um novo `FileContext`.

>[!NOTE]
>Não há nenhum modelo de push para os consumidores. Os consumidores não serão notificados de um provedor novo `FileContext` após sua solicitação.

## <a name="expensive-file-context-computations"></a>Cálculos de contexto de arquivos caras

Conteúdo do arquivo de leitura de disco pode ser caro, especialmente quando um provedor precisa resolver a relação entre arquivos. Por exemplo, um provedor pode ser consultado para o contexto de arquivo do arquivo de alguma origem, mas o contexto do arquivo é dependente de um arquivo de projeto. Analisar o arquivo de projeto ou avaliá-lo com o MSBuild é caro. Em vez disso, a extensão pode exportar uma `IFileScanner` para criar `FileDataValue` dados durante a indexação de espaço de trabalho. Agora quando for solicitado para contextos de arquivo, o `IFileContextProvider` podem consultar rapidamente para que os dados indexados. Para obter mais informações sobre indexação, consulte o [espaço de trabalho de indexação](workspace-indexing.md) tópico.

>[!WARNING]
>Tenha cuidado de outras maneiras de seu `FileContext` podem ser caras de computar. Algumas interações de interface do usuário são síncronas e contam com um alto volume de `FileContext` solicitações. Exemplos incluem abrindo uma guia do editor e abrindo uma **Gerenciador de soluções** menu de contexto. Essas ações Verifique o contexto de build muitas solicitações de tipo.

## <a name="file-context-related-apis"></a>APIs relacionadas ao contexto de arquivo

- <xref:Microsoft.VisualStudio.Workspace.FileContext> mantém os dados e metadados.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> e <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> criar o contexto do arquivo.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Exporta um provedor de contexto do arquivo.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> é usado para os consumidores para obter os contextos de arquivo.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Define os tipos de contexto de build que consumirá Abrir pasta.

## <a name="file-context-actions"></a>Ações de contexto do arquivo

Enquanto um `FileContext` em si é apenas os dados sobre alguns arquivos, um <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> é uma maneira de expressar e agir sobre dados. `IFileContextAction` é flexível em seu uso. Dois dos seus casos mais comuns são compilar e depurar.

## <a name="reporting-progress"></a>Relatório de progresso

O <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> é passado para método `IProgress<IFileContextActionProgressUpdate>`, mas o argumento não deve ser usado como esse tipo. `IFileContextActionProgressUpdate` é uma interface vazia e invocando `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` poderá gerar `NotImplementedException`. Em vez disso, o `IFileContextAction` deve converter o argumento para outro tipo, conforme necessário para o cenário.

Para obter informações sobre os tipos fornecidos pelo Visual Studio, consulte a documentação do respectivo cenário.

## <a name="file-context-action-related-apis"></a>APIs relacionadas à ação de contexto do arquivo

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> executa algum comportamento com base em um `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> cria instâncias de `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Exporta o tipo `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Observação de arquivo

Um espaço de trabalho escuta notificações de alteração de arquivo e fornece o <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Arquivos que correspondem a configuração "ExcludedItems" não produzirá eventos de notificação de arquivo. Um limite entre os eventos é usado para a simplificação de notificação e redução duplicada. Quando você precisa reagir a uma alteração de arquivo, você deve assinar esse serviço.

>[!TIP]
>Um espaço de trabalho [serviço de indexação](workspace-indexing.md) assina os eventos de arquivo por padrão. Arquivo adições e modificações fará com que relevantes `IFileScanner`eventos s a ser invocado para novos dados para esse arquivo. Exclusões de arquivo removerá os dados indexados. Você não precisa assinar seu `IFileScanner` para o serviço do Inspetor de arquivo.

## <a name="next-steps"></a>Próximas etapas

* [Indexação](workspace-indexing.md) -espaço de trabalho de indexação coleta e persiste nas informações sobre o espaço de trabalho.
* [Espaços de trabalho](workspaces.md) -examine os conceitos de espaço de trabalho e configurações de armazenamento.
