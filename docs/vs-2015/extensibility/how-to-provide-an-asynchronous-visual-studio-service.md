---
title: 'Como: fornecer um serviço assíncrono | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204110"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Como fornecer um serviço assíncrono do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você quiser obter um serviço sem bloquear o thread da interface do usuário, deverá criar um serviço assíncrono e carregar o pacote em um thread em segundo plano. Para essa finalidade, você pode usar um <xref:Microsoft.VisualStudio.Shell.AsyncPackage> em vez de um <xref:Microsoft.VisualStudio.Shell.Package> e adicionar o serviço com os métodos assíncronos especiais do pacote assíncrono

 Para obter informações sobre como fornecer serviços síncronos do Visual Studio, consulte [como fornecer um serviço](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implementando um serviço assíncrono

1. Crie um projeto VSIX (**arquivo/novo/projeto/Visual C#/extensiblity/projeto VSIX**). Nomeie o projeto **TestAsync**.

2. Adicione um VSPackage ao projeto. Selecione o nó do projeto na **Gerenciador de soluções** e clique em **Adicionar/novo item/Visual C# itens/extensibilidade/pacote do Visual Studio**. Nomeie esse arquivo **TestAsyncPackage.cs**.

3. Em TestAsyncPackage.cs, altere o pacote para herdar de AsyncPackage em vez de pacote:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Para implementar um serviço, você precisa criar três tipos:

    - Uma interface que descreve o serviço. Muitas dessas interfaces estão vazias, ou seja, não têm métodos.

    - Uma interface que descreve a interface do serviço. Essa interface inclui os métodos a serem implementados.

    - Uma classe que implementa o serviço e a interface de serviço.

5. O exemplo a seguir mostra uma implementação muito básica dos três tipos. O construtor da classe de serviço deve definir o provedor de serviços. Neste exemplo, vamos apenas adicionar o serviço ao arquivo de código do pacote.

6. Adicione as seguintes instruções using ao arquivo de pacote:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Aqui está a implementação do serviço assíncrono. Observe que você precisa definir o provedor de serviços assíncrono em vez do provedor de serviços síncrono no construtor:

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Registrando um serviço
 Para registrar um serviço, adicione o <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> ao pacote que fornece o serviço. Há duas diferenças no registro de um serviço síncrono:

- Se você estiver carregando o pacote com o carregamento automático, deverá adicionar o <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valor BackgroundLoad ao atributo. Para obter mais informações sobre o carregamento automático de VSPackages, consulte [carregando VSPackages](../extensibility/loading-vspackages.md).

- Você deve adicionar o campo **AllowsBackgroundLoading = true** ao <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Para obter mais informações sobre o PackageRegistrationAttribute, consulte [registrando e cancelando o registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

  Aqui está um exemplo de um AsyncPackage com um registro de serviço assíncrono::

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Adicionando um serviço

1. No TestAsyncPackage.cs, remova o `Initialize()` método e substitua o `InitializeAsync()` método. Adicione o serviço e adicione um método de retorno de chamada para criar os serviços. Aqui está um exemplo do inicializador assíncrono adicionando um serviço:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Adicione uma referência a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3. Implemente o método de retorno de chamada como um método assíncrono que cria e retorna o serviço.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Usando um serviço
 Agora você pode obter o serviço e usar seus métodos.

1. Mostraremos isso no inicializador, mas você poderá obter o serviço em qualquer lugar em que desejar usar o serviço.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Não se esqueça de alterar *\<userpath>* para um nome de arquivo e caminho que faça sentido em seu computador!

2. Compile e execute o código. Quando a instância experimental do Visual Studio for exibida, abra uma solução. Isso faz com que o AsyncPackage seja AutoLoad. Quando o inicializador tiver sido executado, você deverá encontrar um arquivo no local especificado.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Usando um serviço assíncrono em um manipulador de comandos
 Aqui está um exemplo de como usar um serviço assíncrono em um comando de menu. Você pode usar o procedimento mostrado aqui para usar o serviço em outros métodos não assíncronos.

1. Adicione um comando de menu ao seu projeto. (No **Gerenciador de soluções**, selecione o nó do projeto, clique com o botão direito do mouse e selecione **Adicionar/novo item/extensibilidade/comando personalizado**.) Nomeie o arquivo de comando **TestAsyncCommand.cs.**

2. O modelo de comando personalizado adiciona novamente o `Initialize()` método ao arquivo TestAsyncPackage.cs para inicializar o comando. No método Initialize (), copie a linha que inicializa o comando. Ele deverá ser parecido com:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Mova essa linha para o `InitializeAsync()` método no arquivo AsyncPackageForService.cs. Como isso está em uma inicialização assíncrona, você deve alternar para o thread principal antes de inicializar o comando usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Agora, ele deve ser assim:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. Exclua o `Initialize()` método.

4. No arquivo TestAsyncCommand.cs, localize o `MenuItemCallback()` método. Exclua o corpo do método.

5. Adicionar uma instrução using:

    ```
    using System.IO;
    ```

6. Adicione um método assíncrono chamado `GetAsyncService()` , que obtém o serviço e usa seus métodos:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Chame esse método do `MenuItemCallback()` método:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Compile a solução e inicie a depuração. Quando a instância experimental do Visual Studio for exibida, vá para o menu **ferramentas** e procure o item de menu **invocar TestAsyncCommand** . Quando você clica nele, o TextWriterService grava no arquivo especificado. (Você não precisa abrir uma solução, pois invocar o comando também faz com que o pacote seja carregado.)

## <a name="see-also"></a>Consulte Também
 [Usando e fornecendo serviços](../extensibility/using-and-providing-services.md)
