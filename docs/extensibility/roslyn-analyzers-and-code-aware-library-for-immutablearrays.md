---
title: Roslyn Analyzers e Biblioteca com reconhecimento de código para ImmutableArrays | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2076bc9fe3cabbfef8d3f3fb0248724835fa83f5
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444564"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analisadores roslyn e biblioteca com reconhecimento de código para ImmutableArrays

A [Plataforma de Compilador .NET](https://github.com/dotnet/roslyn) ("Roslyn") ajuda você a construir bibliotecas com reconhecimento de código. Uma biblioteca com reconhecimento de código fornece funcionalidades que você pode usar e ferramentas (analisadores Roslyn) para ajudá-lo a usar a biblioteca da melhor maneira ou para evitar erros. Este tópico mostra como construir um analisador Roslyn do mundo real para capturar erros comuns ao usar o pacote [System.Collections.Imutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet. O exemplo também demonstra como fornecer uma correção de código para um problema de código encontrado pelo analisador. Os usuários vêem correções de código na ui da lâmpada visual studio e podem aplicar uma correção para o código automaticamente.

## <a name="get-started"></a>Introdução

Você precisa do seguinte para construir este exemplo:

* Visual Studio 2015 (não uma Express Edition) ou uma versão posterior. Você pode usar o [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/) gratuito
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Você também pode, ao instalar o Visual Studio, verificar **ferramentas de extensibilidade do Visual Studio** em Common **Tools** para instalar o SDK ao mesmo tempo. Se você já instalou o Visual Studio, você também pode instalar este SDK indo para o menu principal **Arquivo** > **Novo** > **Projeto,** escolhendo **C#** no painel de navegação à esquerda e, em seguida, escolhendo **Extensibility**. Quando você escolhe o modelo de projeto **" Install the Visual Studio Extensibility Tools**", ele solicita que você baixe e instale o SDK.
* [Plataforma de compilador .NET ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Você também pode instalar este SDK indo para o menu principal **Arquivo** > **Novo** > **Projeto**, escolhendo **C#** no painel de navegação à esquerda e, em seguida, escolhendo **Extensibility**. Quando você escolhe " Baixe o modelo de projeto de projeto de breadcrumb**da plataforma do compilador .NET SDK**", ele solicita que você baixe e instale o SDK. Este SDK inclui o [Visualizador de Sintaxe Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Esta ferramenta útil ajuda você a descobrir quais tipos de modelo de código você deve procurar em seu analisador. A infra-estrutura do analisador chama seu código para tipos específicos de modelo de código, de modo que seu código só é executado quando necessário e pode se concentrar apenas na análise de código relevante.

## <a name="whats-the-problem"></a>Qual é o problema?

Imagine que você forneça uma biblioteca com suporte <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>ao ImmutableArray (por exemplo). Os desenvolvedores C# têm muita experiência com matrizes .NET. No entanto, devido à natureza dos ImmutáveisArrays e técnicas de otimização usadas na implementação, as intuições do desenvolvedor C# fazem com que os usuários de sua biblioteca escrevam código quebrado, como explicado abaixo. Além disso, os usuários não veem seus erros até o tempo de execução, que não é a experiência de qualidade a que estão acostumados no Visual Studio com .NET.

Os usuários estão familiarizados com o código de escrita como o seguinte:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Criar matrizes vazias para preencher com linhas de código subseqüentes e usar a sintaxe inicialização da coleção são familiares aos desenvolvedores C#. No entanto, escrever o mesmo código para um ImmutableArray falha no tempo de execução:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

O primeiro erro deve-se à implementação do ImmutableArray usando uma estrutura para envolver o armazenamento de dados subjacente. Os structs devem ter construtores sem `default(T)` parâmetros para que as expressões possam retornar estruturas com todos os membros zero ou nulos. Quando o código `b1.Length`acessa, há um erro de desreferência nulo em tempo de execução porque não há matriz de armazenamento subjacente na estrutura ImmutableArray. A maneira correta de criar um ImmutableArray vazio é `ImmutableArray<int>.Empty`.

O erro com os iniciadores `ImmutableArray.Add` de cobrança acontece porque o método retorna novas instâncias cada vez que você chamá-lo. Como o ImmutableArrays nunca muda, quando você adiciona um novo elemento, você recebe de volta um novo objeto ImmutableArray (que pode compartilhar o armazenamento por razões de desempenho com um ImmutableArray anteriormente existente). Porque `b2` aponta para o primeiro ImmutableArray antes de ligar `Add()` cinco vezes, `b2` é um ImmutableArray padrão. Chamar comprimento nele também falha com um erro de desreferência nulo. A maneira correta de inicializar um ImmutableArray sem chamar manualmente Add é usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Encontre tipos relevantes de nó de sintaxe para acionar seu analisador

 Para começar a construir o analisador, primeiro descubra que tipo de SintaxNode você precisa procurar. Inicie o Visualizador de **Sintaxe** do menu **Ver** > outros**visualizadores de sintaxe do****Windows** > Roslyn .

Coloque o caret do editor na `b1`linha que declara. Você verá que o Visualizador de Sintaxe mostra que você está em um `LocalDeclarationStatement` nó da árvore de sintaxe. Este nó tem `VariableDeclaration`um , que `VariableDeclarator`por sua vez `EqualsValueClause`tem um , `ObjectCreationExpression`que por sua vez tem um , e finalmente há um . Ao clicar na árvore de nó Sintaxizador visualizador, a sintaxe na janela do editor é destacada para mostrar o código representado por esse nó. Os nomes dos subtipos SintaxNode correspondem aos nomes usados na gramática C#.

## <a name="create-the-analyzer-project"></a>Crie o projeto analisador

No menu principal, escolha **Arquivo** > **Novo** > **Projeto**. No **diálogo Novo Projeto,** em **projetos C#** na barra de navegação à esquerda, escolha **Extensibility**e no painel direito escolha o analisador com modelo de projeto **Code Fix.** Digite um nome e confirme a caixa de diálogo.

O modelo abre um *arquivo DiagnosticAnalyzer.cs.* Escolha a guia buffer do editor. Este arquivo tem uma classe analisador (formada a partir do `DiagnosticAnalyzer` nome que você deu ao projeto) que deriva (de um tipo de API roslyn). Sua nova classe `DiagnosticAnalyzerAttribute` tem uma declaração de que seu analisador é relevante para a linguagem C# para que o compilador descubra e carregue seu analisador.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Você pode implementar um analisador usando o Visual Basic que visa o código C# e vice-versa. É mais importante no DiagnosticAnalyzerAttribute escolher se o analisador tem como alvo um idioma ou ambos. Analisadores mais sofisticados que requerem modelagem detalhada da linguagem só podem atingir uma única língua. Se o seu analisador, por exemplo, apenas verificar nomes de tipos ou nomes de membros públicos, poderá ser possível usar o modelo de linguagem comum que Roslyn oferece em Visual Basic e C#. Por exemplo, o FxCop adverte <xref:System.Runtime.Serialization.ISerializable>que uma classe implementa, mas a classe não tem o atributo <xref:System.SerializableAttribute> é independente de linguagem e funciona tanto para o código Visual Basic quanto para c#.

## <a name="initialize-the-analyzer"></a>Inicialize o analisador

 Desça um `DiagnosticAnalyzer` pouco na `Initialize` classe para ver o método. O compilador chama esse método ao ativar um analisador. O método `AnalysisContext` pega um objeto que permite que seu analisador obtenha informações de contexto e registre retornos de chamadas para eventos para os tipos de código que você deseja analisar.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Abra uma nova linha neste método e digite "contexto". para ver uma lista de conclusão do IntelliSense. Você pode ver na lista `Register...` de conclusão que existem muitos métodos para lidar com vários tipos de eventos. Por exemplo, o `RegisterCodeBlockAction`primeiro, chama de volta para o seu código para um bloco, que geralmente é código entre chaves. O registro de um bloco também chama de volta ao seu código para o inicializador de um campo, o valor dado a um atributo ou o valor de um parâmetro opcional.

Como outro `RegisterCompilationStartAction`exemplo, , chama de volta para o seu código no início de uma compilação, que é útil quando você precisa coletar estado em muitos locais. Você pode criar uma estrutura de dados, por exemplo, para coletar todos os símbolos usados, e cada vez que seu analisador é chamado de volta para alguma sintaxe ou símbolo, você pode salvar informações sobre cada local em sua estrutura de dados. Quando você é chamado de volta devido ao final da compilação, você pode analisar todos os `using` locais que você salvou, por exemplo, para relatar quais símbolos o código usa de cada declaração.

Usando o **Visualizador de Sintaxe,** você aprendeu que deseja ser chamado quando o compilador processa uma ObjectCreationExpression. Você usa este código para configurar o retorno de chamada:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Você registra um nó de sintaxe e filtra apenas para nós de sintaxe de criação de objetos. Por convenção, os autores analisadores usam uma lambda ao registrar ações, o que ajuda a manter os analisadores apátridas. Você pode usar o recurso Visual Studio `AnalyzeObjectCreation` Gerar do **Uso** para criar o método. Isso gera o tipo correto de parâmetro de contexto para você também.

## <a name="set-properties-for-users-of-your-analyzer"></a>Defina propriedades para usuários do seu analisador

Para que seu analisador apareça na Visual Studio UI apropriadamente, procure e modifique a seguinte linha de código para identificar seu analisador:

```csharp
internal const string Category = "Naming";
```

Alterar `"Naming"` para `"API Guidance"`.

Em seguida, encontre e abra o arquivo *Resources.resx* em seu projeto usando o **Solution Explorer**. Você pode colocar uma descrição para o seu analisador, título, etc. Você pode mudar o valor `"Don't use ImmutableArray<T> constructor"` de tudo isso por enquanto. Você pode colocar argumentos de formatação {1}de string em sua `Diagnostic.Create()`seqüência (, `params` {0}, etc.), e mais tarde quando você ligar, você pode fornecer uma matriz de argumentos a serem aprovados.

## <a name="analyze-an-object-creation-expression"></a>Analisar uma expressão de criação de objeto

O `AnalyzeObjectCreation` método leva um tipo diferente de contexto fornecido pela estrutura do analisador de código. O `Initialize` método `AnalysisContext` permite que você registre retornos de ação para configurar seu analisador. O `SyntaxNodeAnalysisContext`, por exemplo, tem um `CancellationToken` que você pode passar por aí. Se um usuário começar a digitar no editor, Roslyn cancelará a execução de analisadores para salvar o trabalho e melhorar o desempenho. Como outro exemplo, este contexto tem uma propriedade Node que retorna o nó de sintaxe de criação de objetos.

Obtenha o nó, que você pode assumir que é o tipo para o qual você filtrou a ação do nó de sintaxe:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Lance o Visual Studio com seu analisador pela primeira vez

Inicie o Visual Studio construindo e executando seu analisador (pressione **F5**). Como o projeto de inicialização no **Solution Explorer** é o projeto VSIX, executar seu código constrói seu código e um VSIX e, em seguida, lança o Visual Studio com o VSIX instalado. Quando você lança o Visual Studio desta forma, ele é lançado com uma colmeia de registro distinta para que seu uso principal do Visual Studio não seja afetado por suas instâncias de teste durante a construção de analisadores. A primeira vez que você lança desta forma, o Visual Studio faz várias inicializações semelhantes às de quando você lançou o Visual Studio depois de instalá-lo.

Crie um projeto de console e, em seguida, insira o código de matriz em seus aplicativos de console Método principal:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

As linhas de `ImmutableArray` código com têm squiggles porque você precisa obter o `using` pacote NuGet imutável e adicionar uma declaração ao seu código. Pressione o botão certo no nó do projeto no **Solution Explorer** e escolha **Gerenciar pacotes NuGet**. No gerenciador NuGet, digite "Imutável" na caixa de pesquisa e escolha o item **System.Collections.Imutável** (não escolha **Microsoft.Bcl.Imutável)** no painel esquerdo e pressione o botão **Instalar** no painel direito. A instalação do pacote adiciona uma referência às referências do projeto.

Você ainda vê rabiscos `ImmutableArray`vermelhos sob , por isso coloque o cuidado nesse identificador e **pressione Ctrl**+**.** (período) para trazer o menu de correção `using` sugerido e optar por adicionar a declaração apropriada.

**Salve tudo e feche** a segunda instância do Visual Studio por enquanto para colocá-lo em um estado limpo para continuar.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Termine o analisador usando edit e continue

Na primeira instância do Visual Studio, defina um `AnalyzeObjectCreation` ponto de ruptura no início do seu método pressionando **F9** com o caret na primeira linha.

Inicie seu analisador novamente com **F5**, e na segunda instância do Visual Studio, reabra seu aplicativo de console que você criou da última vez.

Você retorna à primeira instância do Visual Studio no ponto de ruptura porque o compilador Roslyn viu uma expressão de criação de objeto e chamou seu analisador.

**Pegue o nó de criação de objeto.** Passe por cima da `objectCreation` linha que define a variável pressionando **F10**e na **Janela Imediata** avalie a expressão `"objectCreation.ToString()"`. Você vê que o nó de sintaxe `"new ImmutableArray<int>()"`que a variável aponta é o código , exatamente o que você está procurando.

**Obtenha imutávelArray<\> objeto T Type.** Você precisa verificar se o tipo que está sendo criado é ImmutableArray. Primeiro, você recebe o objeto que representa este tipo. Você verifica tipos usando o modelo semântico para garantir que você tem `ToString()`exatamente o tipo certo, e você não compara a seqüência de . Digite a seguinte linha de código no final da função:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Você designa tipos genéricos em metadados com backticks (') e o número de parâmetros genéricos. É por isso que você não vê "... ImmutableArray\<T>" no nome dos metadados.

O modelo semântico tem muitas coisas úteis nele que permitem que você faça perguntas sobre símbolos, fluxo de dados, vida útil variável, etc. Roslyn separa os nódulos de sintaxe do modelo semântico por várias razões de engenharia (desempenho, modelagem de código errôneo, etc.). Você deseja que o modelo de compilação procure informações contidas em referências para comparação precisa.

Você pode arrastar o ponteiro de execução amarela no lado esquerdo da janela do editor. Arraste-o até a `objectCreation` linha que define a variável e passe sobre sua nova linha de código usando **F10**. Se você passar o ponteiro `immutableArrayOfType`do mouse sobre a variável, verá que encontramos o tipo exato no modelo semântico.

**Obtenha o tipo de expressão de criação de objeto.** "Tipo" é usado de algumas maneiras neste artigo, mas isso significa que se você tem uma expressão "novo Foo", você precisa obter um modelo de Foo. Você precisa obter o tipo de expressão de criação de objeto\<para ver se é o tipo immutávelArray T>. Use novamente o modelo semântico para obter informações de símbolo para o símbolo do tipo (ImmutableArray) na expressão de criação de objetos. Digite a seguinte linha de código no final da função:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Como o analisador precisa lidar com código incompleto ou incorreto nos `using` buffers do `symbolInfo` editor `null`(por exemplo, há uma declaração ausente), você deve verificar se está . Você precisa obter um tipo nomeado (INamedTypeSymbol) do objeto de informações de símbolo para concluir a análise.

**Compare os Tipos.** Como há um tipo genérico aberto de T que estamos procurando, e o tipo no código é um tipo genérico concreto, você consulta as informações `immutableArrayOfTType`do símbolo para o que o tipo é construído (um tipo genérico aberto) e compara esse resultado com . Digite o seguinte no final do método:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Informe o Diagnóstico.** Relatar o diagnóstico é muito fácil. Você usa a Regra criada para você no modelo de projeto, que é definida antes do método Inicializar. Como essa situação no código é um erro, você pode `DiagnosticSeverity.Warning` alterar a linha que `DiagnosticSeverity.Error` inicializou Regra para substituir (squiggle verde) por (squiggle vermelho). O resto da Regra inicia-se a partir dos recursos que você editou perto do início do passo a passo. Você também precisa informar a localização do squiggle, que é a localização da especificação de tipo da expressão de criação de objeto. Digite este `if` código no bloco:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Sua função deve ser assim (talvez formatado de forma diferente):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Remova o ponto de ruptura para que você possa ver seu analisador funcionando (e pare de retornar à primeira instância do Visual Studio). Arraste o ponteiro de execução para o início do seu método e pressione **F5** para continuar a execução. Quando você voltar para a segunda instância do Visual Studio, o compilador começará a examinar o código novamente, e ele chamará em seu analisador. Você pode ver um squiggle sob `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Adicionando uma "Correção de Código" para o Problema de Código

Antes de começar, feche a segunda instância do Visual Studio e pare de depurar na primeira instância do Visual Studio (onde você está desenvolvendo o analisador).

**Adicione uma nova classe.** Use o menu de atalho (botão de ponteiro direito) no nó do projeto no **Solution Explorer** e escolha adicionar um novo item. Adicione uma `BuildCodeFixProvider`classe chamada . Esta classe precisa `CodeFixProvider`derivar , e você precisará usar **Ctrl**+**.** (período) para invocar a correção `using` de código que adiciona a declaração correta. Esta classe também precisa ser anotada com `ExportCodeFixProvider` atributo, e `using` você precisará `LanguageNames` adicionar uma declaração para resolver o enum. Você deve ter um arquivo de classe com o seguinte código nele:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Stub fora membros derivados.** Agora, coloque o cuidado do editor `CodeFixProvider` no identificador e pressione **Ctrl.**+**.** (período) para stub out a implementação para esta classe base abstrata. Isso gera uma propriedade e um método para você.

**Implemente a propriedade.** Preencha o `FixableDiagnosticIds` corpo `get` da propriedade com o seguinte código:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn reúne diagnósticos e correções combinando esses identificadores, que são apenas cordas. O modelo do projeto gerou um ID de diagnóstico para você, e você está livre para alterá-lo. O código na propriedade apenas retorna o ID da classe analisador.

**O método RegisterCodeFixAsync leva um contexto.** O contexto é importante porque uma correção de código pode se aplicar a vários diagnósticos, ou pode haver mais de um problema em uma linha de código. Se você digitar "contexto". no corpo do método, a lista de conclusão do IntelliSense mostrará alguns membros úteis. Há um membro do CancelToken que você pode verificar para ver se algo quer cancelar a correção. Há um membro do Documento que tem muitos membros úteis e permite que você obtenha objetos de modelo de projeto e solução. Há um membro do Span que é o início e o fim do local de código especificado quando você relatou o diagnóstico.

**Faça o método ser assincronte.** A primeira coisa que você precisa fazer é `async` corrigir a declaração do método gerado para ser um método. A correção de código para a implementação de `async` uma classe abstrata não `Task`inclui a palavra-chave, embora o método retorne a .

**Pegue a raiz da árvore de sintaxe.** Para modificar o código, você precisa produzir uma nova árvore de sintaxe com as alterações que sua correção de código faz. Você precisa `Document` do contexto `GetSyntaxRootAsync`para chamar. Este é um método de sincronia porque há trabalho desconhecido para obter a árvore de sintaxe, possivelmente incluindo obter o arquivo do disco, analisá-lo e construir o modelo de código Roslyn para ele. A ID visual studio deve ser responsiva durante este tempo, que utiliza `async` habilita. Substitua a linha de código no método pelo seguinte:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Encontre o nó com o problema.** Você passa no período do contexto, mas o nó que você encontra pode não ser o código que você tem que mudar. O diagnóstico relatado apenas forneceu o intervalo para o identificador do tipo (onde o squiggle `new` pertencia), mas você precisa substituir toda a expressão de criação do objeto, incluindo a palavra-chave no início e os parênteses no final. Adicione o seguinte código ao seu método (e use **Ctrl**+**.** para adicionar `using` uma `ObjectCreationExpressionSyntax`declaração para ):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registre sua correção de código para a ui da lâmpada.** Quando você registra sua correção de código, Roslyn conecta-se automaticamente à iA da lâmpada do Visual Studio. Os usuários finais verão que podem usar **ctrl**+**.** (período) quando o analisador embaralha `ImmutableArray<T>` um mau uso do construtor. Como seu provedor de correção de código só é executado quando há um problema, você pode assumir que tem a expressão de criação de objeto que estava procurando. A partir do parâmetro de contexto, você pode registrar a nova `RegisterCodeFixAsync` correção de código adicionando o seguinte código ao final do método:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Você precisa colocar o cuidado do editor no `CodeAction`identificador, em seguida, usar **Ctrl**+**.** (período) para adicionar `using` a declaração apropriada para este tipo.

Em seguida, coloque o cuidado `ChangeToImmutableArrayEmpty` do editor no identificador e use **Ctrl**+**.** novamente para gerar este stub método para você.

Este último trecho de código que você adicionou `CodeAction` registra a correção de código passando a e o ID de diagnóstico para o tipo de problema encontrado. Neste exemplo, há apenas um ID de diagnóstico para o qual este código fornece correções, para que você possa simplesmente passar o primeiro elemento do array de IDs de diagnóstico. Quando você `CodeAction`cria o , você passa no texto que a iu lâmpada deve usar como uma descrição da correção de código. Você também passa em uma função que pega um Token de Cancelamento e retorna um novo Documento. O novo Documento tem uma nova árvore de sintaxe que inclui seu código remendado que chama `ImmutableArray.Empty`. Este trecho de código usa um lambda para que ele possa fechar sobre o nó objectCreation e o Documento do contexto.

**Construa a nova árvore de sintaxe.** No `ChangeToImmutableArrayEmpty` método cujo stub você gerou anteriormente, `ImmutableArray<int>.Empty;`digite a linha de código: . Se você visualizar a janela da ferramenta **Sintax Visualizer** novamente, poderá ver que essa sintaxe é um nó SimpleMemberAccessExpression. É isso que este método precisa para construir e retornar em um novo Documento.

A primeira `ChangeToImmutableArrayEmpty` mudança é `async` `Task<Document>` adicionar antes porque os geradores de código não podem assumir que o método deve ser assincronido.

Preencha o corpo com o seguinte código para que seu método seja semelhante ao seguinte:

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Você precisará colocar o cuidado do editor `SyntaxGenerator` no identificador e usar **Ctrl**+**.** (período) para adicionar `using` a declaração apropriada para este tipo.

Este código `SyntaxGenerator`usa , que é um tipo útil para a construção de um novo código. Depois de obter um gerador para o `ChangeToImmutableArrayEmpty` `MemberAccessExpression`documento que tem o problema de código, chama , passando o tipo que tem o membro queremos acessar e passando o nome do membro como uma string.

Em seguida, o método busca a raiz do documento, e como isso pode envolver trabalho arbitrário no caso geral, o código aguarda esta chamada e passa o token de cancelamento. Os modelos de código Roslyn são imutáveis, como trabalhar com uma seqüência .NET; quando você atualiza a seqüência, você recebe um novo objeto de seqüência em troca. Quando você `ReplaceNode`ligar, você recebe de volta um novo nó raiz. A maior parte da árvore de sintaxe é compartilhada `objectCreation` (porque é imutável), mas o nó é substituído pelo `memberAccess` nó, assim como todos os nós-pais até a raiz da árvore de sintaxe.

## <a name="try-your-code-fix"></a>Tente sua correção de código

Agora você pode pressionar **F5** para executar seu analisador em uma segunda instância do Visual Studio. Abra o projeto do console que você usou antes. Agora você deve ver a lâmpada aparecer onde `ImmutableArray<int>`sua nova expressão de criação de objeto é para . Se você pressionar **Ctrl**+**.** (período), então você verá sua correção de código, e verá uma visualização de diferença de código gerada automaticamente na ida de luz. Roslyn cria isso para você.

**Dica Pro:** Se você iniciar a segunda instância do Visual Studio e não ver a lâmpada com sua correção de código, então você pode precisar limpar o cache de componentes do Visual Studio. A limpeza do cache força o Visual Studio a reexaminar os componentes, de modo que o Visual Studio deve então pegar seu componente mais recente. Primeiro, desligue a segunda instância do Visual Studio. Em seguida, no **Windows Explorer,** navegue até *\\%LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn*. (O "16.0" muda de versão para versão com o Visual Studio.) Exclua o subdiretório *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Palestra vídeo e projeto de código de acabamento

Você pode ver este exemplo desenvolvido e discutido mais adiante [nesta palestra.](https://channel9.msdn.com/events/Build/2015/3-725) A palestra demonstra o analisador de trabalho e o orienta através da construção.

Você pode ver todo o código acabado [aqui.](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) As subpastas *DoNotUseImmutableArrayCollectionInitializer* e *DoNotUseImmutableArrayCtor* têm cada uma um arquivo C# para encontrar problemas e um arquivo C# que implementa as correções de código que aparecem na ui lâmpada visual studio. Note, o código acabado tem um pouco mais de abstração\<para evitar buscar o objeto immutávelArray T> de tipo mais e mais. Ele usa ações registradas aninhadas para salvar o objeto do tipo em um contexto disponível sempre que as subações (analisar a criação de objetos e analisar inicializações de coleta) forem executadas.

## <a name="see-also"></a>Confira também

* [\\\Construir 2015](https://channel9.msdn.com/events/Build/2015/3-725)
* [Código preenchido no GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Vários exemplos no GitHub, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Outros docs no site do GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Regras do FxCop implementadas com analisadores Roslyn no GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
