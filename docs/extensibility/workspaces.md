---
title: Espaços de trabalho no Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952757"
---
# <a name="workspaces"></a>Workspaces

Um espaço de trabalho é como o Visual Studio representa qualquer coleção de arquivos na [pasta aberta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)e é representado pelo <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo. Por si só, o espaço de trabalho não entende o conteúdo ou os recursos relacionados aos arquivos dentro da pasta. Em vez disso, ele fornece um conjunto geral de APIs para recursos e extensões para produzir e consumir dados com os quais outras pessoas podem agir. Os produtores são compostos por meio do [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) usando vários atributos de exportação.

## <a name="workspace-providers-and-services"></a>Provedores de espaço de trabalho e serviços

Os provedores e serviços de espaço de trabalho fornecem os dados e a funcionalidade para reagir ao conteúdo de um espaço de trabalho. Eles podem fornecer informações de arquivo contextual, símbolos em arquivos de origem ou funcionalidade de compilação.

Ambos os conceitos usam um [padrão de fábrica](https://en.wikipedia.org/wiki/Factory_method_pattern) e são importados por meio do MEF pelo espaço de trabalho. Todos os atributos de exportação implementam `IProviderMetadataBase` ou `IWorkspaceServiceFactoryMetadata` , mas há tipos concretos que as extensões devem usar para tipos exportados.

Uma diferença entre provedores e serviços é sua relação com o espaço de trabalho. Um espaço de trabalho pode ter muitos provedores de um tipo específico, mas apenas um serviço de um tipo específico é criado por espaço de trabalho. Por exemplo, um espaço de trabalho tem muitos provedores de scanner de arquivo, mas o espaço de trabalho tem apenas um serviço de indexação por espaço de trabalho.

Outra diferença importante é o consumo de dados de provedores e serviços. O espaço de trabalho é o ponto de entrada para obter dados de provedores por alguns motivos. Primeiro, os provedores normalmente têm algum conjunto estreito de dados que eles criam. Os dados podem ser símbolos para um arquivo de origem C# ou contextos de arquivo de compilação para um arquivo _CMakeLists.txt_ . O espaço de trabalho corresponderá à solicitação de um consumidor para os provedores cujos metadados se alinham com a solicitação. Em segundo lugar, alguns cenários permitem que muitos provedores contribuam para uma solicitação, enquanto outros cenários usam o provedor com prioridade mais alta.

Por outro lado, as extensões podem obter instâncias do e interagir diretamente com os serviços de espaço de trabalho. Os métodos de extensão `IWorkspace` estão disponíveis para os serviços fornecidos pelo Visual Studio, como <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Sua extensão pode oferecer um serviço de espaço de trabalho para componentes dentro de sua extensão ou para que outras extensões consumam. Os consumidores devem usar <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> ou um método de extensão que você fornecer no `IWorkspace` tipo.

>[!WARNING]
> Não crie serviços que entrem em conflito com o Visual Studio. Isso pode levar a problemas inesperados.

## <a name="disposal-on-workspace-closure"></a>Alienação no fechamento do espaço de trabalho

No fechamento de um espaço de trabalho, talvez os extensores precisem descartar, mas chamar código assíncrono. A <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interface está disponível para facilitar a gravação desse código.

## <a name="related-types"></a>Tipos relacionados

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> é a entidade central para um espaço de trabalho aberto, como uma pasta aberta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Cria um provedor por espaço de trabalho instanciado.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Cria um serviço por espaço de trabalho instanciado.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> deve ser implementado em provedores e serviços que precisam executar código assíncrono durante a alienação.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> fornece métodos auxiliares para acessar serviços bem conhecidos ou serviços arbitrários.

## <a name="workspace-settings"></a>Configurações do workspace

Os espaços de trabalho têm um <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> serviço com controle simples, mas poderoso, sobre um espaço de trabalho. Para obter uma visão geral básica das configurações, consulte [Personalizar tarefas de compilação e depuração](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

As configurações para a maioria dos `SettingsType` tipos são arquivos _. JSON_ , como _VSWorkspaceSettings.jsno_ e _tasks.vs.jsem_.

O poder das configurações do espaço de trabalho se concentra em "escopos", que são simplesmente caminhos dentro do espaço de trabalho. Quando um consumidor chama <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> , todos os escopos que incluem o caminho solicitado e o tipo de configuração são agregados. A prioridade de agregação de escopo é a seguinte:

1. "Configurações locais", que normalmente é o diretório da raiz do espaço de trabalho `.vs` .
1. O próprio caminho solicitado.
1. O diretório pai do caminho solicitado.
1. Todos os diretórios pai adicionais até e incluindo a raiz do espaço de trabalho.
1. "Configurações globais", que está em um diretório de usuário.

O resultado é uma instância do <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Esse objeto contém as configurações para um tipo específico e pode ser consultado quanto à configuração de nomes de chave armazenados como `string` . Os métodos <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> e <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> métodos de extensão esperam que o chamador saiba o tipo do valor de configuração que está sendo solicitado. À medida que a maioria dos arquivos de configurações é persistida como arquivos _. JSON_ , muitas invocações usarão `string` , `bool` , e `int` matrizes desses tipos. Também há suporte para tipos de objeto. Nesses casos, você pode usar `IWorkspaceSettings` a si mesmo como o argumento de tipo. Por exemplo:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Supondo que essas configurações estavam em um _VSWorkspaceSettings.js_do usuário em, os dados podem ser acessados como:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Essas APIs de configurações não estão relacionadas às APIs disponíveis no `Microsoft.VisualStudio.Settings` namespace. As configurações do espaço de trabalho não são independentes do host e usam arquivos de configuração específicos do espaço de trabalho ou provedores de configurações dinâmicas.

### <a name="providing-dynamic-settings"></a>Fornecendo configurações dinâmicas

As extensões podem fornecer <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> s. Esses provedores na memória permitem que as extensões adicionem configurações ou substituam outras.

Exportar um `IWorkspaceSettingsProvider` é diferente de outros provedores de espaço de trabalho. A fábrica não é `IWorkspaceProviderFactory` e não há nenhum tipo de atributo especial. Em vez disso, implemente <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> e use `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Ao implementar métodos que retornam `IWorkspaceSettingsSource` (como `IWorkspaceSettingsProvider.GetSingleSettings` ), retornam uma instância do `IWorkspaceSettings` em vez de `IWorkspaceSettingsSource` . `IWorkspaceSettings` fornece mais informações que podem ser úteis durante algumas agregações de configurações.

### <a name="settings-related-apis"></a>APIs relacionadas a configurações

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> lê e agrega configurações para o espaço de trabalho.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Obtém o `IWorkspaceSettingsManager` para um espaço de trabalho.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Obtém as configurações de um determinado escopo agregado em todos os escopos sobrepostos.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contém configurações para um escopo específico.

## <a name="workspace-suggested-practices"></a>Práticas sugeridas do espaço de trabalho

- Retornar objetos do `IWorkspaceProviderFactory.CreateProvider` ou de APIs semelhantes que se lembram do `Workspace` contexto quando criados. As interfaces de provedores são escritas, esperando que esse objeto seja mantido na criação.
- Salve caches ou configurações específicas do espaço de trabalho no caminho "configurações locais" do espaço de trabalho. Crie um caminho para o arquivo usando o `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` Visual Studio 2017 versão 15,6 ou posterior. Para versões anteriores à versão 15,6, use o seguinte trecho de código:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Eventos da solução e carga automática do pacote

Os pacotes carregados podem implementar `IVsSolutionEvents7` e invocar `IVsSolution.AdviseSolutionEvents` . Ele inclui eventos ao abrir e fechar uma pasta no Visual Studio.

Um contexto de interface do usuário pode ser usado para carregar automaticamente seu pacote. O valor é `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Solução de problemas

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>O pacote SourceExplorerPackage não foi carregado corretamente

A extensibilidade do espaço de trabalho é muito baseada em MEF e os erros de composição farão com que o pacote que hospeda a pasta aberta falhe ao ser carregado. Por exemplo, se uma extensão exporta um tipo com `ExportFileContextProviderAttribute` , mas o tipo só implementa `IWorkspaceProviderFactory<IFileContextActionProvider>` , um erro ocorrerá quando você tentar abrir uma pasta no Visual Studio.

::: moniker range="vs-2017"

Os detalhes do erro podem ser encontrados em _%localappdata%\microsoft\visualstudio\15.0_id \componentmodelcache\microsoft.VisualStudio.default.err_. Resolva quaisquer erros de tipos implementados por sua extensão.

::: moniker-end

::: moniker range=">=vs-2019"

Os detalhes do erro podem ser encontrados em _%localappdata%\microsoft\visualstudio\16.0_id \componentmodelcache\microsoft.VisualStudio.default.err_. Resolva quaisquer erros de tipos implementados por sua extensão.

::: moniker-end

## <a name="next-steps"></a>Próximas etapas

* [Contextos de arquivo](workspace-file-contexts.md) -provedores de contexto de arquivo trazem inteligência de código para espaços de trabalho de pasta aberta.
* [Indexação](workspace-indexing.md) -a indexação do espaço de trabalho coleta e mantém informações sobre o espaço de trabalho.
