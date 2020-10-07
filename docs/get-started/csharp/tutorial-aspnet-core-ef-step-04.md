---
title: 'Etapa 4: expondo uma API Web do seu aplicativo ASP.NET Core'
description: Adicionar uma API Web ao seu aplicativo Web ASP.NET Core com este tutorial em vídeo e instruções passo a passo.
ms.custom: get-started
ms.date: 02/13/2020
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
ms.openlocfilehash: 9a2ee576808698e19726cadfea7ba560ce3bdb7c
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91780934"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Etapa 4: expor uma API Web do seu aplicativo ASP.NET Core

Siga estas etapas para adicionar uma API Web ao seu aplicativo ASP.NET Core existente.

_Assista a este vídeo e acompanhe-o para adicionar suporte a API Web em seu primeiro aplicativo Web ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Abrir o projeto

Abra seu aplicativo ASP.NET Core no Visual Studio 2019. O aplicativo deverá já estar usando o EF Core para gerenciar seus tipos de modelo, conforme configurado na [etapa 3 desta série de tutoriais](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Adicionar um controlador de API

Clique com o botão direito do mouse no projeto e adicione uma nova pasta chamada *Api*. Em seguida, clique com o botão direito do mouse nessa pasta e escolha **Adicionar**  >  **novo item com Scaffold**. Escolha **Controlador de API com ações, usando o Entity Framework.** Agora, escolha uma classe de modelo existente e clique em **Adicionar**.

![Controlador de API gerado por scaffold do ASP.NET Core no Visual Studio 2019](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Examinar o controlador gerado

O código gerado inclui uma nova classe de controlador. Na parte superior da definição de classe há dois atributos.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

O primeiro especifica a rota para ações nesse controlador como `api/[controller]`, o que significa que, se o controlador for denominado `GamesController`, a rota será `api/Games`.

O segundo atributo, `[ApiController]`, adiciona algumas validações úteis à classe, como garantir que cada método de ação inclua seu próprio atributo `[Route]`.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

O controlador usa o `AppDbContext` existente, passado para seu construtor. Cada ação usará esse campo para trabalhar com os dados do aplicativo.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

O primeiro método é uma solicitação GET simples, como especificado usando o atributo `[HttpGet]`. Ele não usa nenhum parâmetro e retorna uma lista de todos os jogos no banco de dados.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

O próximo método especifica `{id}` na rota, o que será adicionado à rota após um `/`, para que a rota completa seja algo como `api/Games/5`, conforme mostrado no comentário na parte superior. A entrada `id` é mapeada para o parâmetro `id` no método. Dentro do método, se o modelo for inválido, um resultado `BadRequest` será retornado. Caso contrário, o EF tentará encontrar o registro correspondente ao `id` fornecido. Se não for possível, um resultado `NotFound` será retornado, caso contrário, o registro `Game` apropriado será retornado.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

Em seguida, uma solicitação `[HttpPut]` feita à API é usada para realizar atualizações. O novo registro `Game` é fornecido no corpo da solicitação. Algumas verificações de validação e erro são executadas e, se tudo for bem-sucedido, o registro no banco de dados será atualizado com os valores fornecidos no corpo da solicitação. Caso contrário, uma resposta de erro apropriada será retornada.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

Uma solicitação `[HttpPost]` é usada para adicionar novos registros ao sistema. Assim como acontece com o `[HttpPut]`, o registro é adicionado no corpo da solicitação. Se ele for válido, o EF Core adicionará o registro ao banco de dados, e a ação retornará o registro atualizado (com sua ID do banco de dados gerada) e um link para o registro na API.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Por fim, uma rota `[HttpDelete]` é usada com uma ID para excluir um registro. Se a solicitação for válida e existir um registro com a ID especificada, o EF Core o excluirá do banco de dados.

## <a name="adding-swagger"></a>Adicionar o Swagger

O Swagger é uma ferramenta de documentação e testes da API que pode ser adicionada como um conjunto de serviços e middleware a um aplicativo ASP.NET Core. Para isso, clique com o botão direito do mouse no projeto e escolha **Gerenciar pacotes NuGet**. Em seguida, clique em **procurar**, procure `Swashbuckle.AspNetCore` e instale a versão 4.0.1.

![Adicionar Swashbuckle do Nuget no Visual Studio de 2019](media/vs-2019/vs2019-nuget-swashbuckle.png)

Uma vez instalado, abra `Startup.cs` e adicione o seguinte ao final do método `ConfigureServices`:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Também é preciso adicionar `using Swashbuckle.AspNetCore.Swagger;` ao início do arquivo.

Em seguida, adicione o seguinte método `Configure`, antes de `UseMvc`:

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.),
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Agora você pode compilar e executar seu aplicativo. No navegador, vá até `/swagger` na barra de endereços. Você deve ver uma lista de modelos e pontos de extremidade de API do seu aplicativo.

![Página do Swagger no navegador no Visual Studio 2019](media/vs-2019/vs2019-swagger-browser.png)

Clique em um ponto de extremidade em Jogos, depois em `Try it out` e `Execute` para ver como os diferentes pontos de extremidade se comportam.

## <a name="next-steps"></a>Próximas etapas

No próximo vídeo, você aprenderá como implantar seu aplicativo no Azure.

[Etapa 5: implantando seu aplicativo ASP.NET Core no Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Confira também

- [Introdução ao Swashbuckle e ao ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio&preserve-view=true)
- [ASP.NET Core páginas de ajuda da API Web com o Swagger/OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2&preserve-view=true)