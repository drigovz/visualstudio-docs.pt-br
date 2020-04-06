---
title: 'Como: Fornecer um Serviço de Estúdio Visual Assíncrono | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710760"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Como: Fornecer um serviço assíncrono do Visual Studio
Se você quiser obter um serviço sem bloquear o segmento de ia, você deve criar um serviço assíncrono e carregar o pacote em um segmento de fundo. Para isso, você <xref:Microsoft.VisualStudio.Shell.AsyncPackage> pode usar <xref:Microsoft.VisualStudio.Shell.Package>um e não um , e adicionar o serviço com os métodos assíncronos especiais do pacote assíncrono.

 Para obter informações sobre como fornecer serviços sincronizados do Visual Studio, consulte [Como: Fornecer um serviço](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementar um serviço assíncrono

1. Crie um projeto VSIX **(Arquivo** > **Novo** > **Projeto** > **Visual C#** > **Extensiblity** > **VSIX Project**). Nomeie o projeto **TestAsync**.

2. Adicione um VSPackage ao projeto. Selecione o nó do projeto no **Solution Explorer** e clique em **Adicionar** > **novo item** > **Visual C# Items** > **Extensibility** > **Visual Studio Package**. Nomeie este arquivo *TestAsyncPackage.cs*.

3. Em *TestAsyncPackage.cs,* altere o `AsyncPackage` pacote `Package`para herdar em vez de :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Para implementar um serviço, você precisa criar três tipos:

    - Uma interface que identifica o serviço. Muitas dessas interfaces estão vazias, ou seja, não têm métodos, pois são usadas apenas para consultar o serviço.

    - Uma interface que descreve a interface de serviço. Esta interface inclui os métodos a serem implementados.

    - Uma classe que implementa tanto o serviço quanto a interface de serviço.

5. O exemplo a seguir mostra uma implementação muito básica dos três tipos. O construtor da classe de serviço deve definir o provedor de serviços. Neste exemplo, vamos apenas adicionar o serviço ao arquivo de código do pacote.

6. Adicione as seguintes diretivas usando o arquivo do pacote:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Aqui está a implementação de serviços assíncronos. Observe que você precisa definir o provedor de serviços assíncrono em vez do provedor de serviços síncrono no construtor:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Registre um serviço
 Para registrar um serviço, adicione o <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pacote que fornece o serviço. Diferente de registrar um serviço síncrono, você tem que ter certeza de que o pacote e o serviço suportam carregamento assíncrono:

- Você deve adicionar o **campo AllowsBackgroundLoading = true** para garantir que o <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> pacote possa ser inicializado de forma assíncrona Para obter mais informações sobre o PackageRegistrationAttribute, consulte Registrar e [descadastrar VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Você deve adicionar o campo **IsAsyncQueryable = true** ao para garantir que a instância de <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> serviço possa ser inicializada de forma assíncrona.

  Aqui está um `AsyncPackage` exemplo de um com um registro de serviço assíncrono:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Adicionar um serviço

1. Em *TestAsyncPackage.cs,* `Initialize()` remova o método `InitializeAsync()` e anule o método. Adicione o serviço e adicione um método de retorno de chamada para criar os serviços. Aqui está um exemplo do inicializador assíncrono adicionando um serviço:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Para tornar este serviço visível fora deste pacote, defina o valor da bandeira de promoção *como* o último parâmetro:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Adicione uma referência ao *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Implemente o método de retorno de chamada como um método assíncrono que cria e retorna o serviço.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Use um serviço
 Agora você pode obter o serviço e usar seus métodos.

1. Vamos mostrar isso no inicializador, mas você pode obter o serviço em qualquer lugar que você quiser usar o serviço.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Não se esqueça `userpath` de mudar para um nome de arquivo e caminho que faz sentido na sua máquina!

2. Construa e execute o código. Quando a instância experimental do Visual Studio aparecer, abra uma solução. Isso faz `AsyncPackage` com que o auto-carregamento. Quando o inicializador for executado, você deve encontrar um arquivo no local especificado.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Use um serviço assíncrono em um manipulador de comando
 Aqui está um exemplo de como usar um serviço assíncrono em um comando de menu. Você pode usar o procedimento mostrado aqui para usar o serviço em outros métodos não assíncronos.

1. Adicione um comando de menu ao seu projeto. (No **Explorador de soluções,** selecione o nó do projeto, clique com o botão direito do mouse e selecione **Adicionar** > novo comando personalizado**de extensibilidade** > **de****item** > .) Nomeie o arquivo de comando *TestAsyncCommand.cs*.

2. O modelo de comando `Initialize()` personalizado adiciona o método ao arquivo *TestAsyncPackage.cs* para inicializar o comando. No `Initialize()` método, copie a linha que inicializa o comando. O resultado deve ser assim:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Mova esta linha `InitializeAsync()` para o método no arquivo *AsyncPackageForService.cs.* Uma vez que esta está em uma inicialização assíncrona, você <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>deve mudar para o segmento principal antes de inicializar o comando usando . Agora, ele deve ser assim:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Exclua `Initialize()` o método.

4. No arquivo *TestAsyncCommand.cs,* `MenuItemCallback()` encontre o método. Exclua o corpo do método.

5. Adicionar uma diretiva de uso:

    ```csharp
    using System.IO;
    ```

6. Adicione um método assíncrono chamado `UseTextWriterAsync()`, que obtém o serviço e usa seus métodos:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Chame este método `MenuItemCallback()` a partir do método:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Compile a solução e inicie a depuração. Quando a instância experimental do Visual Studio aparecer, vá para o menu **Ferramentas** e procure o item do menu **Invocar TestAsyncCommand.** Quando você clica nele, o TextWriterService grava para o arquivo especificado. (Você não precisa abrir uma solução, porque invocar o comando também faz com que o pacote seja carregado.)

## <a name="see-also"></a>Confira também
- [Usar e prestar serviços](../extensibility/using-and-providing-services.md)
