---
title: 'Etapa 3: trabalhando com dados em seu aplicativo ASP.NET Core'
description: Comece a trabalhar com dados usando Entity Framework Core em seu aplicativo Web ASP.NET Core com este tutorial em vídeo e instruções passo a passo.
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
ms.openlocfilehash: 42bc0442dc5901f92fc8a83b7af41c1fc42f4be4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250802"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Etapa 3: trabalhar com dados usando Entity Framework

Siga estas etapas para começar a trabalhar com dados usando Entity Framework Core em seu aplicativo Web ASP.NET Core.

_Assista a este vídeo e siga as instruções para adicionar dados em seu primeiro aplicativo Web ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Abrir o projeto

Se você estiver acompanhando estes vídeos, abra o projeto de aplicativo Web que você criou na seção anterior. Se você estiver começando, precisará criar um novo projeto e escolher **Aplicativo Web ASP.NET** e, em seguida, **aplicativo Web**. Deixe o restante das opções com os padrões.

## <a name="add-your-model"></a>Adicionar o modelo

O primeiro a fazer para trabalhar com dados no aplicativo ASP.NET Core é descrever como devem ser os dados. Chamamos essa criação de *modelo* dos elementos envolvidos no problema que estamos tentando resolver. Em aplicativos reais, adicionaremos lógica de negócios personalizada nesses modelos para que possam se comportam de determinadas maneiras e automatizar tarefas. Neste exemplo, vamos criar um sistema simples para controlar jogos de tabuleiro. Precisamos de uma classe que represente um jogo e inclua algumas propriedades que queremos registrar sobre esse jogo, por exemplo, a quantas pessoas ele pode dar suporte. Essa classe entrará em uma nova pasta que criaremos na raiz do projeto da Web, chamada *Modelos*.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Criar as páginas para gerenciar sua biblioteca de jogos

Agora estamos prontos para criar as páginas que usaremos para gerenciar nossa biblioteca de jogos. Isso pode parecer intimidador, mas é surpreendentemente fácil. Primeiro, precisamos decidir onde em nosso aplicativo essa funcionalidade deve residir. Abra a pasta Páginas no projeto da Web e adicione uma nova pasta lá. Chame-a de *Jogos*.

Agora, clique com o botão direito do mouse em jogos e escolha **Adicionar**  >  **novo item com Scaffold**. Escolha as Razor Pages usando a opção **Entity Framework (CRUD)**. CRUD significa "Criar, ler, atualizar, excluir", e este modelo criará páginas para cada uma dessas operações (incluindo uma página "Listar tudo" e uma página "Exibir detalhes de um item").

![Adicionar páginas geradas por scaffold do ASP.NET Core no Visual Studio 2019](media/vs-2019/vs2019-add-scaffold.png)

Selecione sua classe de modelo Jogo e use o ícone “+” para adicionar uma nova classe de contexto de dados. Nomeie-o `AppDbContext`. Mantenha os outros padrões e clique em **Adicionar**.

Você verá que as seguintes Razor Pages adicionadas à pasta Jogos:

- Create.cshtml
- Delete.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Páginas geradas por scaffold do ASP.NET Core no Visual Studio 2019](media/vs-2019/vs2019-scaffolded-pages.png)

Além de adicionar páginas na pasta *Jogos*, a operação de scaffolding adicionou código à minha classe *Startup.cs*. Examinando o método `ConfigureServices` nessa classe, você verá que este código foi adicionado:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Você também descobrirá que a cadeia de conexão `AppDbContext` foi adicionada ao arquivo *appsettings.json* do projeto.

Se você executar o aplicativo agora, ele poderá falhar porque nenhum banco de dados foi criado ainda. Você pode configurar o aplicativo para criar automaticamente o banco de dados, se for necessário ao [adicionar código a Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main):

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

Para resolver os typenames no código anterior, adicione as seguintes instruções using a *Program.cs* no final do bloco existente de instruções using:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Use o nome do seu projeto, em vez de WebApplication1 em seu código.

A maior parte do código é apenas para tratamento de erro e para fornecer acesso ao EF Core `AppDbContext` antes que o aplicativo entre em execução. A linha importante é a que diz `context.Database.EnsureCreated()`, que criará o banco de dados se ele ainda não existir. Agora, o aplicativo está pronto para ser executado.

## <a name="test-it-out"></a>Teste-o

Execute o aplicativo e navegue para `/Games` na barra de endereços. Você verá uma página de lista vazia. Selecione **Criar Novo** para adicionar um novo `Game` à coleção. Preencha o formulário e clique em **Criar**. Você deve vê-lo na exibição de lista. Clique em **Detalhes** para ver os detalhes de um único registro.

Adicione outro registro. Você pode clicar em *Editar* para alterar os detalhes de um registro ou em **Excluir** para removê-lo, o que solicitará uma confirmação antes da exclusão do registro.

![Páginas geradas por scaffold do ASP.NET Core no Visual Studio 2019 no navegador](media/vs-2019/vs2019-game-list.png)

Isso é o necessário para começar a trabalhar com dados em um aplicativo ASP.NET Core usando EF Core e Visual Studio 2019.

## <a name="next-steps"></a>Próximas etapas

No próximo vídeo, você aprenderá como adicionar suporte à API Web em seu aplicativo.

[Etapa 4: expondo uma API Web do seu aplicativo ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Confira também

- [Razor Pages com o Entity Framework Core no ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [Razor Pages do ASP.NET Core com EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
