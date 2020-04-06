---
title: 'Como: Usar o AsyncPackage para carregar VSPacotes em segundo plano | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710623"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Como: Usar o AsyncPackage para carregar VSPackages em segundo plano
Carregar e inicializar um pacote VS pode resultar em I/O de disco. Se tal I/O acontecer no segmento de IA, isso pode levar a problemas de resposta. Para resolver isso, o Visual Studio <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 2015 introduziu a classe que permite o carregamento de pacotes em um segmento de fundo.

## <a name="create-an-asyncpackage"></a>Criar um Pacote De Sincronização
 Você pode começar criando um projeto VSIX **(File** > **New** > **Project** > Visual**C#** > **Extensibility** > **VSIX Project)** e adicionando um VSPackage ao projeto (clique com o botão direito do mouse no projeto e **adicione** > **novo item** > **C# item** > **Extensibility** > **Visual Studio Package).** Em seguida, você pode criar seus serviços e adicionar esses serviços ao seu pacote.

1. Obtenha o <xref:Microsoft.VisualStudio.Shell.AsyncPackage>pacote de .

2. Se você estiver fornecendo serviços cuja consulta pode fazer com que seu pacote seja carregado:

    Para indicar ao Visual Studio que seu pacote é seguro para <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> carregamento em segundo plano e para optar por esse comportamento, você deve definir **AllowsBackgroundLoading** propriedade para true no construtor de atributos.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Para indicar ao Visual Studio que é seguro instanciar seu <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> serviço em um <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> segmento de fundo, você deve definir a propriedade como verdadeira na construtora.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Se você estiver carregando através de contextos de Interface do Usuário, <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> então você deve especificar **PackageAutoLoadFlags.BackgroundLoad** para o OR o valor (0x2) nos sinalizadores escritos como o valor da entrada de carga automática do pacote.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Se você tem um trabalho de inicialização assíncrona para fazer, você deve substituir <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Remova `Initialize()` o método fornecido pelo modelo VSIX. (O `Initialize()` método em **AsyncPackage** está selado). Você pode usar <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> qualquer um dos métodos para adicionar serviços assíncronos ao seu pacote.

    NOTA: `base.InitializeAsync()`Para ligar, você pode alterar seu código-fonte para:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Você deve tomar cuidado para NÃO fazer RPCs (Remote Procedure Call) a partir do seu código de inicialização assíncrona (em **InitializeAsync**). Isso pode ocorrer <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> quando você liga direta ou indiretamente.  Quando forem necessárias cargas de sincronização, a linha de ia de ui bloqueará o uso <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. O modelo de bloqueio padrão desativa os RPCs. Isso significa que se você tentar usar um RPC de suas tarefas de sincronia, você ficará impasse se o segmento de UI estiver esperando o seu pacote carregar. A alternativa geral é empacotar seu código para o segmento de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> IA se necessário usando algo como O Fábrica de **Tarefas Joinable**ou algum outro mecanismo que não use um RPC.  NÃO use **ThreadHelper.Generic.Invoque** ou bloqueie geralmente o segmento de chamada esperando para chegar ao segmento de UI.

    NOTA: Você deve evitar usar **getservice** ou **queryService** em seu `InitializeAsync` método. Se você tiver que usá-los, você precisará mudar para o segmento de ia primeiro. A alternativa é <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> usar a partir do seu <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> **AsyncPackage** (lançando-o para .)

   C#: Criar um Pacote De Sincronização:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Converta um VSPackage existente em AsyncPackage
 A maioria do trabalho é o mesmo que criar um novo **AsyncPackage**. Siga os passos 1 a 5 acima. Você também precisa tomar cuidado extra com as seguintes recomendações:

1. Lembre-se `Initialize` de remover a substituição que você tinha em seu pacote.

2. Evite impasses: Pode haver RPCs escondidos em seu código. que agora acontecem em um segmento de fundo. Certifique-se de que se você estiver fazendo um RPC (por exemplo, **GetService),** você precisa alternar para o segmento principal ou (2) usar a versão assíncrona da API se existir (por exemplo, **GetServiceAsync**).

3. Não alternar entre os fios com muita freqüência. Tente localizar o trabalho que pode acontecer em um segmento de fundo para reduzir o tempo de carga.

## <a name="querying-services-from-asyncpackage"></a>Consultando serviços do AsyncPackage
 Um **AsyncPackage** pode ou não carregar assíncronamente dependendo do chamador. Por exemplo,

- Se o chamador chamado **GetService** ou **QueryService** (ambas APIs síncronas) ou

- Se o chamador chamado **IVsShell::LoadPackage** (ou **IVsShell5:LoadPackageWithContext**) ou

- A carga é acionada por um contexto de Interface do UI, mas você não especificou que o mecanismo de contexto de interface do iu pode carregá-lo assíncronamente

  então seu pacote será carregado sincronicamente.

  Seu pacote ainda tem uma oportunidade (em sua fase de inicialização assíncrona) de fazer o trabalho fora do segmento de UI, embora o segmento de UI será bloqueado para a conclusão desse trabalho. Se o chamador usar **o IAsyncServiceProvider** para consultar assíncronamente o seu serviço, então sua carga e inicialização serão feitas de forma assíncrona, assumindo que eles não bloqueiam imediatamente o objeto de tarefa resultante.

  C#: Como consultar o serviço de forma assíncrona:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
