---
title: 'Etapa 2: criando seu primeiro aplicativo Web ASP.NET Core'
description: Crie seu primeiro aplicativo Web ASP.NET Core com este tutorial em vídeo e instruções passo a passo.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 21052d59205c7ddc14247f180348fea3b8d5652a
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833241"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Etapa 2: criar seu primeiro aplicativo Web ASP.NET Core

Crie seu primeiro aplicativo Web ASP.NET Core com este tutorial em vídeo e instruções passo a passo.

_Assista a este vídeo e acompanhe-o para criar seu primeiro aplicativo Web ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Iniciar o Visual Studio 2019 e criar um projeto

Inicie o Visual Studio 2019 e clique em **Criar um projeto**. Escolha **Aplicativo Web ASP.NET Core**. Escolha o modelo **Aplicativo Web** e mantenha o nome e local padrão do projeto. No menu suspenso com a versão ASP.NET Core, escolha **ASP.NET Core 2,1** ou **ASP.NET Core 2,2**. Clique em **Criar**. Para obter instruções mais detalhadas, consulte o [vídeo anterior nesta série de tutoriais](tutorial-aspnet-core-ef-step-01.md).

![Escolher opções de projeto ASP.NET Core no Visual Studio 2019](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Certifique-se de escolher ASP .NET Core 2,1 ou ASP.NET Core 2,2. Este tutorial não é compatível com o ASP.NET Core 3. x.

## <a name="explore-the-new-project"></a>Explorar o novo projeto

Na janela do gerenciador de soluções, à direita, você pode exibir os conteúdos do novo projeto. Eles são descritos aqui.

![Projeto do ASP.NET Core no Visual Studio 2019](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

A pasta *wwwroot* contém arquivos estáticos que estarão publicamente acessíveis do aplicativo Web. Normalmente, ele contém folhas de estilo, arquivos de script do lado do cliente e imagens.

### <a name="pages"></a>Páginas

A pasta *Pages* contém as Razor Pages do site. O modelo padrão fornece várias páginas, incluindo a página *Index.cshtml* que é a home page do aplicativo, bem como Sobre, Contato e assim por diante.

### <a name="appsettingsjson"></a>appsettings.json

Esse arquivo contém as definições de configuração do site, no formato JSON.

### <a name="programcs"></a>Module.vb

Esse arquivo age como o ponto de entrada para o aplicativo. Quando o aplicativo é executado, o método Main é o primeiro método que é executado e é responsável por criar o Host da Web que conterá o aplicativo.

### <a name="startupcs"></a>Startup.cs

O Host da Web criado no *Program.cs* faz referência à classe Startup e chama os respectivos métodos para configurar o aplicativo. O método ConfigureServices é responsável por configurar quaisquer serviços que o aplicativo usará. O método `Configure` configura o pipeline de solicitação HTTP do aplicativo. Cada solicitação passa por esse pipeline e, conforme o faz, interage com cada parte do *middleware*.

### <a name="indexcshtml"></a>Index.cshtml

A home page para o site inclui um pouco de marcação HTML e algum código do Razor do lado servidor. Ele usa o Razor para especificar o modelo de página, `IndexModel`, que está localizado no arquivo *Index.cshtml.cs* associado. Ele também define o título da página, definindo um valor em ViewData. Esse valor ViewData é lido no arquivo *\_ layout. cshtml* , localizado na pasta compartilhada dentro da pasta páginas. O arquivo de Layout é compartilhado por várias Razor Pages e fornece a aparência e experiência comuns para o aplicativo. O conteúdo de cada página é renderizado dentro HTML do arquivo de Layout.

## <a name="run-the-application"></a>Execute o aplicativo

Agora execute o aplicativo e exiba-o no navegador. Você pode executar o aplicativo usando **Ctrl** + **F5** ou escolhendo **depurar**  >  **Iniciar sem Depurar** no menu do Visual Studio.

## <a name="customize-the-application"></a>Personalizar o aplicativo

Adicione uma propriedade ao arquivo *Index.cshtml.cs* e defina seu valor para a hora atual no manipulador `OnGet`:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Substitua o conteúdo de `<div>` em *Index.cshtml* por esta marcação:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Execute o aplicativo novamente. Você deve ver a página agora exibindo a hora atual, mas é sempre meia-noite! Isso não está certo.

![Captura de tela da home page do aplicativo em uma janela do navegador. O conteúdo da página é lido: "é 12:00 agora mesmo no servidor!".](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Depurar o aplicativo

Adicione um ponto de interrupção para o método `OnGet` no local em que estamos atribuindo um valor para `Time` e, dessa vez, comece a depurar o aplicativo.

A execução é interrompida na linha e você pode ver que `DateTime.Today` inclui a data, mas a hora sempre é meia-noite, porque ele não inclui dados de horário.

![Captura de tela mostrando o código para Index.cshtml.cs no Visual Studio. Um ponto de interrupção é definido na linha, ' time = DateTime. Today. ToShortTimeString (); '.](media/vs-2019/vs2019-breakpoint.png)

Altere-o para usar `DateTime.Now` e continue a executar. O novo código para `OnGet` deve ser:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Agora você deve ver o tempo real do servidor no navegador quando você navega para o aplicativo.

> [!NOTE]
> Sua saída pode diferir da imagem, já que o formato de saída de ToShortDateTimeString depende da configuração de cultura atual. Consulte <xref:System.DateTime.ToShortTimeString>.

![Captura de tela da home page do aplicativo em uma janela do navegador. O conteúdo da página é lido: "é 1:46 agora mesmo no servidor!".](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Próximas etapas

No próximo vídeo, você aprenderá como adicionar suporte a dados em seu aplicativo.

[Tutorial: trabalhando com dados em seu aplicativo ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Consulte também

- [Tutorial: criar um aplicativo Web Razor Pages com ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)
