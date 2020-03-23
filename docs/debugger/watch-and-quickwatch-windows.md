---
title: Defina um relógio nas variáveis | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302003"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Veja variáveis com watch windows e QuickWatch

Enquanto você está depurando, você pode usar **watch** windows e **QuickWatch** para observar variáveis e expressões. As janelas só estão disponíveis durante uma sessão de depuração.

**As** janelas do relógio podem exibir várias variáveis ao mesmo tempo durante a depuração. A caixa de diálogo **QuickWatch** exibe uma única variável de cada vez e deve ser fechada antes que a depuração possa continuar.

Se esta é a primeira vez que você tenta depurar código, você pode querer ler [Depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md) e [técnicas e ferramentas de depuração](../debugger/write-better-code-with-visual-studio.md) antes de passar por este artigo.

## <a name="observe-variables-with-a-watch-window"></a>Observe variáveis com uma janela de relógio

Você pode abrir mais de uma janela **do relógio** e observar mais de uma variável em uma janela **do relógio.**

Por exemplo, para definir um `a`relógio `b`nos `c` valores de , e no seguinte código:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Defina um ponto `c = a + b;` de breakpoint na linha clicando na margem esquerda, selecionando **Debug** > **Toggle Breakpoint**ou pressionando **F9**.

1. Inicie a depuração selecionando a **seta** inicial ou > **depuração de depuração de** **depuração**verde ou pressione **F5**. A execução faz uma pausa no ponto de ruptura.

1. Abra uma janela **do relógio** selecionando **Debug** > **Windows** > **Watch** > Watch**1**ou pressionando **Ctrl**+**Alt**+**W** > **1**.

   Você pode abrir janelas adicionais **do relógio** selecionando janelas **2,** **3**ou **4**.

1. Na janela **Relógio,** selecione uma linha `a`vazia e digite variável . Faça o `b` mesmo `c`por e.

   ![Ver variáveis](../debugger/media/watchvariables.png "WatchVariables")

1. Continue a depurar selecionando **Debug** > **Step Into** ou pressionando **F11** conforme necessário para avançar. Os valores variáveis na janela **Relógio** mudam `for` à medida que você itera através do loop.

>[!NOTE]
>Somente para C++,
>- Você pode precisar qualificar o contexto de um nome variável ou uma expressão que use um nome variável. O contexto é a função, arquivo de origem ou módulo onde uma variável está localizada. Se você tiver que qualificar o contexto, use a sintaxe do [operador de contexto (C++)](../debugger/context-operator-cpp.md) na janela **Nome** na janela **Relógio.**
>
>- Você pode adicionar nomes de registro e nomes de variáveis usando ** $ \<>de nome&nbsp;de registro** ou ** @ \<nome de registro&nbsp;>** para o **Nome** na janela **Relógio.** Para obter mais informações, consulte [Pseudovariáveis](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Use expressões em uma janela do relógio

Você pode observar qualquer expressão válida reconhecida pelo depurador em uma janela **do relógio.**

Por exemplo, para o código na seção anterior, você pode `(a + b + c) / 3` obter a média dos três valores inserindo na janela **Relógio:**

![Expressão do relógio](../debugger/media/watchexpression.png "Expressão do relógio")

As regras para avaliar expressões na janela **relógio** são geralmente as mesmas que as regras para avaliar expressões na linguagem de código. Se uma expressão tiver um erro de sintaxe, espere o mesmo erro de compilador que no editor de código. Por exemplo, um erro de digitação na expressão anterior produz esse erro na janela **Relógio:**

![Erro de expressão do relógio](../debugger/media/watchexpressionerror.png "Erro de expressão do relógio")

Um círculo com dois ícones de linhas onduladas pode aparecer na janela **do relógio.** Este ícone significa que o depurador não avalia a expressão devido a uma potencial dependência de segmentos cruzados. Avaliar o código requer que outros threads do seu aplicativo sejam executados temporariamente, mas como você está no modo de quebra, todos os threads do seu aplicativo geralmente são interrompidos. Permitir que outros segmentos sejam executados temporariamente pode ter efeitos inesperados no estado do seu aplicativo, e o depurador pode ignorar eventos como pontos de interrupção e exceções nesses segmentos.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Pesquisar na janela do relógio

Você pode procurar palavras-chave nas colunas Nome, Valor e Tipo da janela **Do relógio** usando a barra de pesquisa acima de cada janela. Aperte ENTER ou selecione uma das setas para executar uma pesquisa. Para cancelar uma pesquisa em andamento, selecione o ícone "x" na barra de pesquisa.

Use as setas esquerda e direita (Shift+F3 e F3, respectivamente) para navegar entre as partidas encontradas.

![Pesquisar na janela do relógio](../debugger/media/ee-search-watch.png "Pesquisar na janela do relógio")

Para tornar sua pesquisa mais ou menos completa, use a queda **de pesquisa mais profunda** na parte superior da janela do **relógio** para selecionar quantos níveis de profundidade você deseja pesquisar em objetos aninhados. 

## <a name="pin-properties-in-the-watch-window"></a>Propriedades do pino na janela do relógio

>[!NOTE]
> Esse recurso é suportado no .NET Core 3.0 ou superior.

Você pode inspecionar rapidamente objetos por suas propriedades na janela do relógio com a ferramenta **Propriedades Pinnable.**  Para usar esta ferramenta, gire sobre uma propriedade e selecione o ícone de pino que aparece ou clique com o botão direito do mouse e selecione a opção **Membro Pin como Favorito** no menu de contexto resultante.  Isso borbulha essa propriedade no topo da lista de propriedades do objeto, e o nome e valor da propriedade é exibido na coluna **Valor.**  Para desfixar uma propriedade, selecione novamente o ícone de pino ou selecione a opção **Unpin Member como Favorito** no menu contexto.

![Propriedades do pino na janela do relógio](../debugger/media/basic-pin-watch.gif "Propriedades do pino na janela do relógio")

Você também pode alternar nomes de propriedades e filtrar propriedades não fixadas ao visualizar a lista de propriedades do objeto na janela Relógio.  Você pode acessar ambas as opções selecionando os botões na barra de ferramentas acima da janela do relógio.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Atualizar os valores do relógio

Um ícone de atualização (seta circular) pode aparecer na janela **do relógio** quando uma expressão é avaliada. O ícone de atualização indica um erro ou um valor que está desatualizado.

Para atualizar o valor, selecione o ícone de atualização ou pressione a barra de espaço. O depurador tenta reavaliar a expressão. No entanto, você pode não querer ou ser capaz de reavaliar a expressão, dependendo do motivo pelo qual o valor não foi avaliado.

Passar o tempo sobre o ícone de atualização ou ver a coluna **Valor** pela razão pela qual a expressão não foi avaliada. Os motivos incluem:

- Ocorreu um erro quando a expressão estava sendo avaliada, como no exemplo anterior. Um tempo pode ocorrer, ou uma variável pode estar fora de alcance.

- A expressão tem uma chamada de função que pode desencadear um efeito colateral no aplicativo. Consulte [Os efeitos colaterais da expressão](#bkmk_sideEffects).

- A avaliação automática das propriedades e das chamadas de função implícita está desativada.

Se o ícone de atualização aparecer porque a avaliação automática das propriedades e chamadas de função implícita estiver desativada, você poderá habilitá-lo selecionando **Ativar avaliação de propriedade e outras chamadas de função implícitas** em **Ferramentas** > **Opções** > **Depuração** > **Geral**.

Para demonstrar usando o ícone de atualização:

1. Em **Ferramentas** > **Depuração** > **geral**de**opções,** > limpe a **avaliação de propriedade ativar e outras chamadas de função implícitas.**

1. Digite o código a seguir e, na `list.Count` janela **Relógio,** defina um relógio na propriedade.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Inicie a depuração. A janela **Relógio** mostra algo como a seguinte mensagem:

   ![Relógio de atualização](../debugger/media/refreshwatch.png "Relógio de atualização")

1. Para atualizar o valor, selecione o ícone de atualização ou pressione a barra de espaço. O depurador reavalia a expressão.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Efeitos colaterais de expressão

Avaliar algumas expressões pode alterar o valor de uma variável, ou afetar o estado do seu aplicativo. Por exemplo, avaliar a expressão a seguir altera o valor de `var1`:

```csharp
var1 = var2
```

Este código pode causar um [efeito colateral.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) Efeitos colaterais podem dificultar a depuração alterando a forma como seu aplicativo opera.

Uma expressão com efeitos colaterais é avaliada apenas uma vez, quando você entra pela primeira vez. Depois disso, a expressão aparece acinzentada na janela do **relógio,** e outras avaliações são desativadas. A coluna Dica de Ferramenta ou **Valor** explica que a expressão causa um efeito colateral. Você pode forçar a reavaliação selecionando o ícone de atualização que aparece ao lado do valor.

Uma maneira de evitar a designação de efeitos colaterais é desligar a avaliação automática da função. Em **Ferramentas** > **Depuração** > **Debugging** > **geral,** desmarque **Habilitar avaliação de propriedade e outras chamadas de função implícitas**.

Somente para C#, quando a avaliação de propriedades ou chamadas de função implícita é desligada, você pode forçar a avaliação adicionando o modificador de formato **ac** a uma variável **Nome** na janela **Do relógio.** Consulte [especificadores de formato em C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Use IDs de objeto na janela do relógio (C# e Visual Basic)

Às vezes você quer observar o comportamento de um objeto específico. Por exemplo, você pode querer rastrear um objeto referido por uma variável local depois que essa variável tiver saído do escopo. Em C# e Visual Basic, você pode criar IDs de objeto para instâncias específicas de tipos de referência e usá-los na janela **do relógio** e em condições de ponto de ruptura. O ID do objeto é gerado pelos serviços de depuração de tempo de execução de idioma comum (CLR) e associado ao objeto.

> [!NOTE]
> Os IDs do objeto criam referências fracas que não impedem que o objeto seja coletado lixo. Eles são válidos apenas para a sessão de depuração atual.

No código a `MakePerson()` seguir, `Person` o método cria um uso de uma variável local:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

Para descobrir o nome `Person` do `DoSomething()` método, você pode adicionar `Person` uma referência ao ID do objeto na janela **do relógio.**

1. Defina um ponto de `Person` ruptura no código após a criação do objeto.

1. Inicie a depuração.

1. Quando a execução for pausada no ponto de ruptura, abra a janela **Locals** escolhendo **Debug** > **Windows** > **Locals**.

1. Na janela **Locals,** clique `Person` com o botão direito do mouse na variável e selecione **Fazer ID de objeto**.

   Você deve ver um**$** sinal de dólar ( ) mais um número na janela **Locais,** que é o ID do objeto.

1. Adicione o ID do objeto à janela **do relógio** clicando com o botão direito do mouse no ID do objeto e selecionando **Adicionar relógio**.

1. Defina outro ponto `DoSomething()` de ruptura no método.

1. Continue a depuração. Quando a execução `DoSomething()` é pausada no `Person` método, a janela **relógio** exibe o objeto.

   > [!NOTE]
   > Se você quiser ver as propriedades do `Person.Name`objeto, como, você deve habilitar a avaliação de propriedades selecionando**Opções de** >  **ferramentas** > **Depuração** > **geral** > **Habilitar avaliação de propriedade e outras chamadas de função implícita**.

## <a name="dynamic-view-and-the-watch-window"></a>Visão dinâmica e a janela do relógio

Algumas linguagens de script (por exemplo, JavaScript ou Python) usam digitação dinâmica ou [de pato,](https://en.wikipedia.org/wiki/Duck_typing) e a versão .NET 4.0 e posteriormente suporta objetos que são difíceis de observar nas janelas normais de depuração.

A janela **Relógio** exibe esses objetos como objetos dinâmicos, que são criados a partir de tipos que implementam a <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Nós de objetodinâmicos mostram os membros dinâmicos dos objetos dinâmicos, mas não permitem a edição dos valores do membro.

Para atualizar os valores **do Dynamic View,** selecione o [ícone de atualização](#bkmk_refreshWatch) ao lado do nó dinâmico do objeto.

Para exibir apenas a **exibição dinâmica de** um objeto, adicione um especificador de formato **dinâmico** após o nome do objeto dinâmico na janela **Relógio:**

- Para C#: `ObjectName, dynamic`
- Para o Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- O depurador C# não reavalia automaticamente os valores na **Exibição Dinâmica** quando você pisa para a próxima linha de código.
>- O depurador Visual Basic atualiza automaticamente as expressões adicionadas através da **Exibição Dinâmica**.
>- A avaliação dos membros de um **Modo de Exibição Dinâmico** pode ter [efeitos colaterais](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Para inserir uma nova variável de relógio que lança um objeto a um objeto dinâmico:**

1. Clique com o botão direito do mouse em qualquer criança de uma **exibição dinâmica**.
1. Escolha **adicionar relógio**. O `object.name` `((dynamic) object).name` vira e aparece em uma nova janela **do relógio.**

O depurador também adiciona um nó de criança **Dynamic View** do objeto à janela **Autos.** Para abrir a janela **Autos,** durante a depuração, selecione **Depurar** > **Autos do****Windows** > .

**O Dynamic View** também melhora a depuração de objetos COM. Quando o depurador chega a um objeto COM embrulhado no **System.__ComObject,** ele adiciona um nó **de exibição dinâmica** para o objeto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observe uma única variável ou expressão com QuickWatch

Você pode usar **o QuickWatch** para observar uma única variável.

Por exemplo, para o seguinte código:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

Para observar `a` a variável,

1. Defina um ponto de interrupção na linha `a = a + b;`.

1. Inicie a depuração. A execução faz uma pausa no ponto de ruptura.

1. Selecione `a` a variável no código.

1. Selecione **Debug** > **QuickWatch,** **pressione Shift**+**F9**ou clique com o botão direito do mouse e selecione **QuickWatch**.

   A caixa de diálogo **QuickWatch** é exibida. A `a` variável está na caixa **Expressão** com um **Valor** de **1**.

   ![Variável QuickWatch](../debugger/media/quickwatchvariable.png "Variável QuickWatch")

1. Para avaliar uma expressão usando a variável, digite uma expressão como `a + b` na caixa **Expressão** e selecione **Reavaliar**.

   ![Expressão QuickWatch](../debugger/media/quickwatchexpression.png "Expressão QuickWatch")

1. Para adicionar a variável ou expressão do **QuickWatch** à janela **do relógio,** **selecione Adicionar relógio**.

1. Selecione **Fechar** para fechar a janela **QuickWatch.** (**QuickWatch** é um diálogo modal, portanto, você não pode continuar a depurar enquanto estiver aberto.)

1. Continue a depuração. Você pode observar a variável na janela **do relógio.**

## <a name="see-also"></a>Confira também
- [O que é depuração?](../debugger/what-is-debugging.md)
- [Ferramentas e técnicas de depuração](../debugger/write-better-code-with-visual-studio.md)
- [Primeira olhada na depuração](../debugger/debugger-feature-tour.md)
- [Janelas de depurador](../debugger/debugger-windows.md)
