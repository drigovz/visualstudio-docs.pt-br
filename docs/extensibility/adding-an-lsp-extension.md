---
title: Adicionando uma extensão do Protocolo do Servidor de Idioma | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740238"
---
# <a name="add-a-language-server-protocol-extension"></a>Adicionar uma extensão do Language Server Protocol

O Language Server Protocol (LSP) é um protocolo comum, sob a forma de JSON RPC v2.0, usado para fornecer recursos de serviço de idioma para vários editores de código. Usando o protocolo, os desenvolvedores podem escrever um único servidor de idiomas para fornecer recursos de serviço de idioma como o IntelliSense, diagnósticos de erros, encontrar todas as referências e assim por diante, para vários editores de código que suportam o LSP. Tradicionalmente, os serviços de idioma no Visual Studio podem ser adicionados usando arquivos de gramática textMate para fornecer funcionalidades básicas, como destaque de sintaxe ou escrevendo serviços de linguagem personalizados que usam o conjunto completo de APIs de extensibilidade do Visual Studio para fornecer dados mais ricos. Com suporte ao Visual Studio para LSP, há uma terceira opção.

![serviço de protocolo de servidor de idiomas no Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Language Server Protocol

![implementação do protocolo do servidor de idiomas](media/lsp-implementation.png)

Este artigo descreve como criar uma extensão do Visual Studio que usa um servidor de idioma baseado em LSP. Ele assume que você já desenvolveu um servidor de idioma baseado em LSP e só quer integrá-lo ao Visual Studio.

Para obter suporte no Visual Studio, os servidores de idiomas podem se comunicar com o cliente (Visual Studio) através de qualquer mecanismo de transmissão baseado em fluxo, por exemplo:

* Fluxos padrão de entrada/saída
* Pipes nomeados
* Soquetes (somente TCP)

A intenção do LSP e do suporte para ele no Visual Studio é a de serviços de linguagem a bordo que não fazem parte do produto Visual Studio. Não se destina a estender os serviços de linguagem existentes (como C#) no Visual Studio. Para estender os idiomas existentes, consulte o guia de extensibilidade do serviço de idiomas (por exemplo, a ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) ou consulte [Estender o editor e os serviços de idiomas](../extensibility/extending-the-editor-and-language-services.md).

Para obter mais informações sobre o protocolo em si, consulte a documentação [aqui](https://github.com/Microsoft/language-server-protocol).

Para obter mais informações sobre como criar um servidor de linguagem de exemplo ou como integrar um servidor de idioma existente no Visual Studio Code, consulte a documentação [aqui](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Recursos suportados pelo Language Server Protocol

As tabelas a seguir mostram quais recursos do LSP são suportados no Visual Studio:

Mensagem | Tem suporte no Visual Studio
--- | ---
Inicializar | sim
inicializado | sim
shutdown | sim
exit | sim
$/cancelAsolicitação | sim
janela/showMessage | sim
janela/showMessageRequest | sim
janela/logMessage | sim
telemetria/evento |
cliente/registroCapacidade |
client/unregisterCapability |
espaço de trabalho/didChangeConfiguração | sim
espaço de trabalho/didChangeWatchedFiles | sim
espaço de trabalho/símbolo | sim
espaço de trabalho/executeCommand | sim
espaço de trabalho/aplicarEdit | sim
textDocument/publicaDiagnósticos | sim
textDocument/didOpen | sim
textDocument/didChange | sim
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sim
textDocument/didClose | sim
textDocument/completion | sim
conclusão/resolução | sim
textDocument/hover | sim
textDocument/assinaturaAjuda | sim
textDocument/references | sim
textDocument/documentHighlight | sim
textDocument/documentSymbol | sim
textDocument/formatação | sim
textDocument/rangeFormatting | sim
textDocument/onTypeFormatting |
textDocument/definição | sim
textDocument/codeAction | sim
textDocument/codeLens |
codeLens/resolver |
textDocument/documentLink |
documentLink/resolve |
textDocument/renome | sim

## <a name="get-started"></a>Introdução

> [!NOTE]
> Começando com o Visual Studio 2017 versão 15.8, o suporte para o Protocolo de Servidor de Linguagem comum é incorporado ao Visual Studio. Se você construiu extensões LSP usando a versão [VSIX do Language Server Client,](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) elas pararão de funcionar assim que você atualizar para a versão 15.8 ou superior. Você precisará fazer o seguinte para que suas extensões de LSP voltem a funcionar:
>
> 1. Desinstale o Microsoft Visual Studio Language Protocol Protocol VSIX.
>
>    A partir da versão 15.8, cada vez que você executa uma atualização no Visual Studio, a visualização VSIX é automaticamente detectada e removida.
>
> 2. Atualize sua referência nuget para a versão não-visualização mais recente para [pacotes LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Remova a dependência do Microsoft Visual Studio Language Server Protocol Preview VSIX em seu manifesto VSIX.
>
> 4. Certifique-se de que seu VSIX especifique visual studio versão 15.8 Preview 3 como o limite inferior para o destino de instalação.
>
> 5. Recompilar e reimplantar.

### <a name="create-a-vsix-project"></a>Crie um projeto VSIX

Para criar uma extensão de serviço de idioma usando um servidor de idioma baseado em LSP, primeiro certifique-se de ter a carga de trabalho de desenvolvimento de **extensão do Visual Studio** instalada para a sua instância de VS.

Em seguida, crie um novo projeto VSIX navegando para **arquivar o** > **novo projeto** > **Visual C#** > **Extensibility** > **VSIX Project**:

![criar projeto vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalação do servidor de idiomas e tempo de execução

Por padrão, as extensões criadas para suportar servidores de idioma baseados em LSP no Visual Studio não contêm os próprios servidores de idioma ou os tempos de execução necessários para executá-los. Os desenvolvedores de extensão são responsáveis pela distribuição dos servidores de idioma e dos tempos de execução necessários. Há várias maneiras de fazê-lo:

* Os servidores de idioma podem ser incorporados no VSIX como arquivos de conteúdo.
* Crie um MSI para instalar o servidor de idiomas e/ou tempos de execução necessários.
* Forneça instruções sobre o Marketplace informando aos usuários como obter tempos de execução e servidores de idioma.

### <a name="textmate-grammar-files"></a>Arquivos de gramática textMate

O LSP não inclui especificações sobre como fornecer coloração de texto para idiomas. Para fornecer colorização personalizada para idiomas no Visual Studio, os desenvolvedores de extensão podem usar um arquivo de gramática TextMate. Para adicionar gramática ou arquivos temáticos personalizados do TextMate, siga estas etapas:

1. Crie uma pasta chamada "Gramáticas" dentro de sua extensão (ou pode ser o nome que você escolher).

2. Dentro da pasta *Gramáticas,* inclua qualquer * \*.tmlanguage*, * \*.plist*, * \*.tmtheme*ou * \*.json* arquivos que você gostaria que fornecessem colorização personalizada.

   > [!TIP]
   > Um arquivo *.tmtheme* define como os escopos mapeiam as classificações do Visual Studio (chamadas chaves de cores). Para orientação, você pode referenciar o arquivo global *.tmtheme* no diretório *%ProgramFiles(x86)%\Microsoft\\\<Visual Studio>\\ \<SKU>\Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg.*

3. Crie um arquivo *.pkgdef* e adicione uma linha semelhante a esta:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Clique com o botão direito do mouse nos arquivos e selecione **Propriedades**. Alterar a ação **Construir** para **Conteúdo** e alterar a propriedade Incluir na propriedade **VSIX** para **true**.

Depois de completar as *etapas* anteriores, uma pasta gramática sacada é adicionada ao diretório de instalação do pacote como uma fonte de repositório chamada 'MyLang' ('MyLang' é apenas um nome para desambiguização e pode ser qualquer string única). Todas as gramáticas *(arquivos .tmlanguage)* e arquivos temáticos *(arquivos .tmtheme)* neste diretório são captadas como potenciais e superam as gramáticas incorporadas fornecidas com o TextMate. Se as extensões declaradas do arquivo de gramática corresponderem à extensão do arquivo que está sendo aberto, o TextMate entrará em serviço.

## <a name="create-a-simple-language-client"></a>Crie um cliente de idioma simples

### <a name="main-interface---ilanguageclient"></a>Interface principal - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Depois de criar seu projeto VSIX, adicione os seguintes pacotes NuGet ao seu projeto:

* [Microsoft.visualStudio.LanguageServer.client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Quando você se baseia no pacote NuGet depois de completar as etapas anteriores, os pacotes Newtonsoft.Json e StreamJsonRpc também são adicionados ao seu projeto. **Não atualize esses pacotes a menos que tenha certeza de que essas novas versões serão instaladas na versão do Visual Studio que sua extensão tem como alvo**. As assembléias não serão incluídas em seu VSIX; em vez disso, eles serão recolhidos do diretório de instalação do Visual Studio. Se você estiver fazendo referência a uma versão mais recente dos conjuntos do que a instalada na máquina de um usuário, sua extensão não funcionará.

Em seguida, você pode criar uma nova classe que implemente a interface [ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) que é a interface principal necessária para clientes de idiomas que se conectam a um servidor de idioma baseado em LSP.

Veja o exemplo a seguir:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Os principais métodos que precisam ser implementados são [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) e [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [O OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) é chamado quando o Visual Studio carregou sua extensão e seu servidor de idiomas está pronto para ser iniciado. Neste método, você pode invocar o delegado [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) imediatamente para sinalizar que o servidor de idioma deve ser iniciado, ou você pode fazer uma lógica adicional e invocar [startAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) mais tarde. **Para ativar seu servidor de idiomas, você deve chamar StartAsync em algum momento.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) é o método eventualmente invocado chamando o delegado [StartAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) Ele contém a lógica para iniciar o servidor de idiomas e estabelecer conexão com ele. Um objeto de conexão que contenha fluxos para escrever para o servidor e leitura do servidor deve ser devolvido. Quaisquer exceções lançadas aqui são capturadas e exibidas ao usuário através de uma mensagem InfoBar no Visual Studio.

### <a name="activation"></a>Ativação

Uma vez que sua classe de cliente de idioma seja implementada, você precisará definir dois atributos para que ela defina como ela será carregada no Visual Studio e ativada:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

O Visual Studio usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) para gerenciar seus pontos de extensibilidade. O atributo [Export](/dotnet/api/system.componentmodel.composition.exportattribute) indica ao Visual Studio que esta classe deve ser recolhida como ponto de extensão e carregada no momento apropriado.

Para usar o MEF, você também deve definir MEF como um Ativo no manifesto VSIX.

Abra seu designer de manifesto VSIX e navegue até a guia **Ativos:**

![adicionar ativo MEF](media/lsp-add-asset.png)

Clique **em Novo** para criar um novo ativo:

![definir ativo MEF](media/lsp-define-asset.png)

* **Tipo:** Microsoft.VisualStudio.MefComponent
* **Fonte**: Um projeto na solução atual
* **Projeto**: [Seu projeto]

### <a name="content-type-definition"></a>Definição de tipo de conteúdo

Atualmente, a única maneira de carregar a extensão do servidor de idioma baseado em LSP é por tipo de conteúdo de arquivo. Ou seja, ao definir sua classe de cliente de idioma (que implementa [o ILanguageClient),](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)você precisará definir os tipos de arquivos que, quando abertos, farão com que sua extensão seja carregada. Se nenhum arquivo compatível com o seu tipo de conteúdo definido for aberto, então sua extensão não será carregada.

Isso é feito através `ContentTypeDefinition` da definição de uma ou mais classes:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;

        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

No exemplo anterior, uma definição de tipo de conteúdo é criada para arquivos que terminam em extensão de arquivo *.bar.* A definição do tipo de conteúdo recebe o nome "barra" e deve derivar de [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Depois de adicionar uma definição de tipo de conteúdo, você pode definir quando carregar a extensão do cliente do idioma na classe cliente do idioma:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Adicionar suporte para servidores de idioma SSP não requer que você implemente seu próprio sistema de projeto no Visual Studio. Os clientes podem abrir um único arquivo ou uma pasta no Visual Studio para começar a usar seu serviço de idioma. Na verdade, o suporte para servidores de idioma SSP foi projetado para funcionar apenas em cenários abertos de pasta/arquivo. Se um sistema de projeto personalizado for implementado, alguns recursos (como configurações) não funcionarão.

## <a name="advanced-features"></a>Recursos avançados

### <a name="settings"></a>Configurações

O suporte para configurações personalizadas específicas do servidor de idiomas está disponível, mas ainda está em processo de melhoria. As configurações são específicas para o que o servidor de idiomas suporta e geralmente controlam como o servidor de idiomaem dados. Por exemplo, um servidor de idiomapode ter uma configuração para o número máximo de erros relatados. Os autores de extensão definiriam um valor padrão, que pode ser alterado pelos usuários para projetos específicos.

Siga estas etapas abaixo para adicionar suporte para configurações à sua extensão de serviço de idioma LSP:

1. Adicione um arquivo JSON (por exemplo, *MockLanguageExtensionSettings.json*) ao seu projeto que contém as configurações e seus valores padrão. Por exemplo:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Clique com o botão direito do mouse no arquivo JSON e selecione **Propriedades**. Altere a ação **Build** para "Conteúdo" e a propriedade "Incluir na propriedade VSIX" para **true**.

3. Implementar ConfiguraçõesSeções e retornar a lista de prefixos para as configurações definidas no arquivo JSON (No Visual Studio Code, isso mapearia para o nome da seção de configuração em package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Adicione um arquivo .pkgdef ao projeto (adicione novo arquivo de texto e altere a extensão do arquivo para .pkgdef). O arquivo pkgdef deve conter esta informação:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Exemplo:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Clique com o botão direito do mouse no arquivo .pkgdef e selecione **Propriedades**. Alterar a ação **Build** para **Conteúdo** e incluir na propriedade **VSIX** para **true**.

6. Abra o arquivo *source.extension.vsixmanifest* e adicione um ativo na guia **Ativo:**

   ![editar vspackage ativo](media/lsp-add-vspackage-asset.png)

   * **Tipo:** Microsoft.VisualStudio.VsPackage
   * **Fonte**: Arquivo no sistema de arquivos
   * **Caminho:**[Caminho para o seu arquivo *.pkgdef]*

### <a name="user-editing-of-settings-for-a-workspace"></a>Edição do usuário de configurações para um espaço de trabalho

1. O usuário abre um espaço de trabalho contendo arquivos que seu servidor possui.
2. O usuário adiciona um arquivo na pasta *.vs* chamada *VSWorkspaceSettings.json*.
3. O usuário adiciona uma linha ao arquivo *VSWorkspaceSettings.json* para uma configuração que o servidor fornece. Por exemplo:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Habilite o rastreamento de diagnósticos

O rastreamento de diagnósticos pode ser habilitado para produzir todas as mensagens entre o cliente e o servidor, o que pode ser útil ao depurar problemas. Para habilitar o rastreamento de diagnóstico, faça o seguinte:

1. Abra ou crie o arquivo de configurações de espaço de trabalho *VSWorkspaceSettings.json* (consulte "Edição do usuário de configurações para um espaço de trabalho").
2. Adicione a seguinte linha no arquivo json de configurações:

```json
{
    "foo.trace.server": "Off"
}
```

Existem três valores possíveis para verbosidade de rastreamento:

* "Desligado": rastreamento desligado completamente
* "Mensagens": rastreamento ligado, mas apenas nome do método e ID de resposta são rastreados.
* "Verbose": rastreamento ligado; toda a mensagem rpc é rastreada.

Quando o rastreamento é ligado, o conteúdo é gravado em um arquivo no diretório *%temp%\VisualStudio\LSP.* O log segue o formato de nomeação *[LanguageClientName]-[Datetime Stamp].log*. Atualmente, o rastreamento só pode ser habilitado para cenários de pasta aberta. Abrir um único arquivo para ativar um servidor de idioma não tem suporte para rastreamento de diagnósticos.

### <a name="custom-messages"></a>Mensagens personalizadas

Existem APIs em vigor para facilitar a passagem de mensagens e o recebimento de mensagens do servidor de idiomas que não fazem parte do Protocolo padrão do Servidor de Idiomas. Para lidar com mensagens personalizadas, implemente a interface [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) na sua classe cliente de idioma. A biblioteca [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) é usada para transmitir mensagens personalizadas entre seu cliente de idioma e servidor de idiomas. Uma vez que a extensão do cliente de idioma SSP é como qualquer outra extensão do Visual Studio, você pode decidir adicionar recursos adicionais (que não são suportados pelo LSP) ao Visual Studio (usando outras APIs do Visual Studio) em sua extensão através de mensagens personalizadas.

#### <a name="receive-custom-messages"></a>Receba mensagens personalizadas

Para receber mensagens personalizadas do servidor de idiomas, implemente a propriedade [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) no [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) e retorne um objeto que saiba como lidar com suas mensagens personalizadas. Exemplo abaixo:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="send-custom-messages"></a>Enviar mensagens personalizadas

Para enviar mensagens personalizadas para o servidor de idiomas, implemente o método [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) no [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Este método é invocado quando seu servidor de idiomas é iniciado e pronto para receber mensagens. Um objeto [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) é passado como um parâmetro, que você pode manter para enviar mensagens para o servidor de idiomas usando [APIs VS-StreamJsonRpc.](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Exemplo abaixo:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Camada média

Às vezes, um desenvolvedor de extensão pode querer interceptar mensagens LSP enviadas e recebidas do servidor de idiomas. Por exemplo, um desenvolvedor de extensão pode querer alterar o parâmetro de mensagem enviado para uma mensagem LSP específica ou modificar os resultados retornados do servidor de idiomas para um recurso DeSp (por exemplo, conclusões). Quando isso for necessário, os desenvolvedores de extensão podem usar a API MiddleLayer para interceptar mensagens LSP.

Cada mensagem LSP tem sua própria interface de camada média para interceptação. Para interceptar uma mensagem específica, crie uma classe que implemente a interface de camada média para essa mensagem. Em seguida, implemente a interface [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) na sua classe cliente de idioma e retorne uma instância do seu objeto na propriedade [MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Exemplo abaixo:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

O recurso de camada média ainda está em desenvolvimento e ainda não é abrangente.

## <a name="sample-lsp-language-server-extension"></a>Extensão do servidor de idioma SSP de exemplo

Para ver o código fonte de uma extensão de amostra usando a API do cliente LSP no Visual Studio, consulte a [amostra LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)VSSDK-Extensibility-Samples .

## <a name="faq"></a>Perguntas frequentes

**Eu gostaria de construir um sistema de projeto personalizado para complementar meu servidor de idiomas LSP para fornecer suporte a recursos mais rico no Visual Studio, como faço para fazer isso?**

O suporte para servidores de idioma baseados em LSP no Visual Studio depende do [recurso de pasta aberta](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) e foi projetado para não exigir um sistema de projeto personalizado. Você pode construir seu próprio sistema de projeto personalizado seguindo instruções [aqui,](https://github.com/Microsoft/VSProjectSystem)mas alguns recursos, como configurações, podem não funcionar. A lógica de inicialização padrão para servidores de idioma SSP é passar no local de pasta raiz da pasta que está sendo aberta atualmente, portanto, se você usar um sistema de projeto personalizado, você pode precisar fornecer lógica personalizada durante a inicialização para garantir que seu servidor de idiomas possa começar corretamente.

**Como adicionar suporte a depurador?**

Forneceremos suporte para o [protocolo comum de depuração](https://code.visualstudio.com/docs/extensionAPI/api-debugging) em uma versão futura.

**Se já houver um serviço de linguagem suportado por VS instalado (por exemplo, JavaScript), ainda posso instalar uma extensão de servidor de idioma SSP que oferece recursos adicionais (como fiação)?**

Sim, mas nem todos os recursos funcionarão corretamente. O objetivo final das extensões do servidor de idiomas LSP é habilitar serviços de idioma não suportados nativamente pelo Visual Studio. Você pode criar extensões que oferecem suporte adicional usando servidores de idioma LSP, mas alguns recursos (como o IntelliSense) não serão uma experiência suave. Em geral, é aconselhável que as extensões do servidor de idioma SSP sejam usadas para fornecer novas experiências linguísticas, não estender as existentes.

**Onde publico meu servidor de idioma SSP completo VSIX?**

Veja as instruções do Marketplace [aqui](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Confira também

- [Adicionar suporte para outras linguagens ao editor do Visual Studio](../ide/adding-visual-studio-editor-support-for-other-languages.md)
