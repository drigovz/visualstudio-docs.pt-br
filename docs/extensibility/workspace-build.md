---
title: Build do espaço de trabalho no Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553322"
---
# <a name="workspace-build"></a>Build do espaço de trabalho

O suporte à compilação em cenários de [pasta aberta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) requer um extensor para fornecer dados de [contexto de arquivo](workspace-file-contexts.md) e [indexados](workspace-indexing.md) para o [espaço de trabalho](workspaces.md), bem como a ação de compilação a ser executada.

Abaixo está uma descrição do que será necessário para sua extensão.

## <a name="build-file-context"></a>Contexto do arquivo de compilação

- Fábrica de provedores
  - `ExportFileContextProviderAttribute` atributo com `supportedContextTypeGuids` como todas as `string` constantes aplicáveis de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Provedor de contexto de arquivo
    - Retornar um `FileContext` para cada operação de compilação e configuração com suporte
      - `contextType` de <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> com a `Configuration` propriedade como a configuração de compilação (por exemplo `"Debug|x86"` , `"ret"` ou `null` se não aplicável). Como alternativa, use uma instância do <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . O valor de configuração **deve** corresponder à configuração do valor de dados de arquivo indexado.

## <a name="indexed-build-file-data-value"></a>Valor de dados de arquivo de compilação indexado

- Fábrica de provedores
  - `ExportFileScannerAttribute` atributo com `IReadOnlyCollection<FileDataValue>` como um tipo com suporte
  - Implementa `IWorkspaceProviderFactory<IFileScanner>`
- Scanner de arquivo em `ScanContentAsync<T>`
  - Retorna dados quando `FileScannerTypeConstants.FileDataValuesType` é o argumento de tipo
  - Retorna um valor de dados de arquivo para cada configuração construída com:
    - `type` como `BuildConfigurationContext.ContextTypeGuid`
    - `context` como sua configuração de compilação (por exemplo `"Debug|x86"` , `"ret"` ou `null` se não aplicável). Esse valor **deve** corresponder à configuração do contexto do arquivo.

## <a name="build-file-context-action"></a>Ação de contexto do arquivo de compilação

- Fábrica de provedores
  - `ExportFileContextActionProvider` atributo com `supportedContextTypeGuids` como todas as `string` constantes aplicáveis de `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Provedor de ações em `IFileContextActionProvider.GetActionsAsync`
  - Retornar um `IFileContextAction` que corresponda ao `FileContext.ContextType` valor especificado
- Ação de contexto de arquivo
  - Implementa `IFileContextAction` e <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` retorno da propriedade `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` é `0x1000` para compilação, `0x1010` para recompilação ou `0x1020` para limpeza

>[!NOTE]
>Como o `FileDataValue` precisa ser indexado, haverá um período de tempo entre a abertura do espaço de trabalho e o ponto no qual o arquivo é examinado quanto à funcionalidade de compilação completa. O atraso será visto na primeira abertura de uma pasta porque não há nenhum índice armazenado em cache anteriormente.

## <a name="reporting-messages-from-a-build"></a>Relatando mensagens de uma compilação

A compilação pode trazer informações, avisos e mensagens de erro para os usuários de uma de duas maneiras. A maneira simples é usar o <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> e fornecer um <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> , da seguinte forma:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` e `BuildMessage.LogMessage` controlar o comportamento de onde as informações são apresentadas ao usuário. Qualquer `BuildMessage.TaskType` valor que não seja `None` produzir uma entrada de **lista de erros** com os detalhes fornecidos. `LogMessage` sempre será apresentado no painel de **compilação** da janela de ferramenta de **saída** .

Como alternativa, as extensões podem interagir diretamente com o **lista de erros** ou o painel de **compilação** . Existe um bug em versões anteriores ao Visual Studio 2017 versão 15,7, em que o `pszProjectUniqueName` argumento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> é ignorado.

>[!WARNING]
>Os chamadores do `IFileContextAction.ExecuteAsync` podem fornecer implementações subjacentes arbitrárias para o `IProgress<IFileContextActionProgressUpdate>` argumento. Nunca invocar `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` diretamente. Atualmente, não há nenhuma diretriz geral para usar esse argumento, mas essas diretrizes estão sujeitas a alterações.

## <a name="build-related-apis"></a>Compilar APIs relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> fornece detalhes de configuração de compilação.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> mostra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> os s para os usuários.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.jse launch.vs.jsem

Para obter informações sobre como criar um tasks.vs.jsou launch.vs.jsno arquivo, consulte [Personalizar tarefas de compilação e depuração](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Próximas etapas

* [Protocolo de servidor de linguagem](language-server-protocol.md) -saiba como integrar os servidores de idiomas ao Visual Studio.