---
title: Definir uma inspeção nas variáveis no Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/11/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad08799c0dce3792e096291dfaf62d52e2515df4
ms.sourcegitcommit: 48bc8492973e93612e5afaba3b47d0f98aecf97c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49325010"
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Definir uma inspeção nas variáveis usando as janelas inspeção e QuickWatch no Visual Studio

Enquanto você estiver depurando, você pode usar o **Watch** e **QuickWatch** windows para inspecionar variáveis e expressões.  A diferença é que o **Watch** janela pode exibir diversas variáveis, enquanto o **QuickWatch** janela exibe uma única variável por vez.

Os windows estão disponíveis somente durante uma sessão de depuração. Para abrir o **Watch** janela, escolha **Debug** > **Windows** > **inspeção**e, em seguida, escolha **Assistir 1**, **Assista 2**, **Assista 3**, ou **Assista 4**. Para abrir o **QuickWatch** janela, ou a variável com o botão direito e escolha **QuickWatch**, ou escolher apenas **depurar** > **QuickWatch** .

## <a name="observe-variables-with-the-watch-window"></a>Observe as variáveis com a janela Inspeção

Você pode observar mais de uma variável com o **inspeção** janela. Por exemplo, se você tiver o seguinte código:

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

Adicione os valores das três variáveis para o **inspeção** janela da seguinte maneira:

1. Selecione o `c = a + b;` linha.

2. Defina um ponto de interrupção (escolhendo **Debug** > **alternar ponto de interrupção** ou pressionando F9).

3. Inicie a depuração (F5). Interrompe a execução no ponto de interrupção.

4. Abra o **Watch** janela (escolhendo **Debug** > **Windows** > **inspeção**  >   **Inspeção 1**, ou pressionando Ctrl + Alt + W, 1).

5. Selecione uma linha vazia e a variável de tipo `a`. Em seguida, fazer a mesma coisa para variáveis `b` e `c`.

   ![Assista a variáveis](../debugger/media/watchvariables.png "WatchVariables")

6. Continue a depuração pressionando F11, conforme necessário, para avançar o depurador.

Você deve ver os valores das variáveis e alterado conforme você itera através de `for` loop.

Se você estiver programando em código nativo, às vezes, você talvez precise qualificar o contexto de um nome de variável ou uma expressão que tem um nome de variável. O contexto é a função, o arquivo de origem e o módulo onde se encontra uma variável. Se você tiver qualificar o contexto, você pode usar a sintaxe do operador de contexto. Para obter mais informações, consulte [operador de contexto (C++)](../debugger/context-operator-cpp.md).

## <a name="observe-expressions-with-the-watch-window"></a>Observar expressões com a janela Inspeção

Agora vamos tentar usar uma expressão em vez disso. Você pode adicionar qualquer expressão válida reconhecida pelo depurador.

Por exemplo, se você tiver o código listado na seção anterior, você pode obter a média dos três valores, usando esta expressão:

![Expressão de inspeção](../debugger/media/watchexpression.png "WatchExpression")

As regras para avaliar expressões na **inspeção** janela geralmente são as mesmas regras para avaliar expressões na linguagem de codificação. Se a expressão possui um erro de sintaxe, esperar que o erro do compilador mesmo que você veria no editor de códigos. Veja um exemplo:

![Assista a erro de expressão](../debugger/media/watchexpressionerror.png "WatchExpressionError")

## <a name="bkmk_refreshWatch"></a> Atualizar valores de inspeção estão desatualizados

Um ícone de atualização (uma seta circular) poderá aparecer quando uma expressão é avaliada na **inspeção** janela. Se você tiver desativado a avaliação da propriedade (escolhendo **ferramentas** > **opções** > **depuração**  >   **Gerais**, em seguida, desmarcando **habilitar avaliação de propriedade e outras chamadas de função implícitas**), e escreveu o código a seguir:

```csharp
static void Main(string[] args)
{
    List<string> list = new List<string>();
    list.Add("hello");
    list.Add("goodbye");
}

```

Você verá algo parecido com a imagem a seguir se você definir uma inspeção no `Count` propriedade da lista:

![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")

A ilustração anterior mostra um erro ou um valor que está desatualizado. Geralmente, você pode atualizar o valor, selecionando o ícone, mas em alguns casos, você talvez prefira não para atualizá-la. Primeiro, você precisa saber por que o valor não foi avaliado.

Uma dica de ferramenta fornece informações sobre por que a expressão não era avaliada se você apontar para o ícone. Se as setas de circundamento aparecerem, a expressão não era avaliada para um dos seguintes motivos:

- Ocorreu um erro porque a expressão estava sendo avaliada. Por exemplo, um tempo limite pode ter ocorrido, ou uma variável pode ter ficado fora do escopo.

- A expressão tem uma chamada de função, que pode disparar um efeito colateral no aplicativo (consulte a [efeitos colaterais e expressões](#bkmk_sideEffects) seção).

- Você tiver desativado a avaliação automática das propriedades e chamadas de função implícitas pelo depurador (escolhendo **ferramentas** > **opções** > **dedepuração**  >  **Gerais**, em seguida, desmarcando **habilitar avaliação de propriedade e outras chamadas de função implícitas**). A expressão não pode ser avaliada automaticamente, em seguida.

Para atualizar o valor, selecione o ícone de atualização, ou pressione a barra de espaços. O depurador tenta reavaliar a expressão. O ícone de atualização pode aparecer porque a avaliação automática de propriedades e outras chamadas de função implícita foi desativada. Nesse caso, o depurador pode avaliar a expressão.

Pode aparecer um ícone que é um círculo com duas linhas onduladas cordas. Este ícone significa que o depurador não avalia a expressão devido à dependência potencial entre threads. Em outras palavras, a avaliar o código requer outros threads em seu aplicativo sejam executados temporariamente. Quando você está no modo de interrupção, todos os threads em seu aplicativo normalmente estão parados. Permitir que outros threads sejam executados temporariamente pode ter inesperado de efeitos sobre o estado do seu programa e faz com que o depurador ignorar eventos como pontos de interrupção e as exceções geradas nesses threads.

## <a name="bkmk_sideEffects"></a> Efeitos colaterais e expressões

Avaliar algumas expressões pode alterar o valor de uma variável ou, de outra forma, afetar o estado do programa. Por exemplo, avaliar a expressão a seguir altera o valor de `var1`:

```csharp
var1 = var2
```

Esse código pode causar uma [efeito colateral](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efeitos colaterais podem dificultar a depuração mais alterando o modo de que operação do seu programa.

Uma expressão conhecida por ter efeitos colaterais é avaliada apenas uma vez, quando você primeiro inseri-la. Avaliações adicionais estão desabilitadas. Manualmente, você pode substituir esse comportamento selecionando o ícone de atualização que aparece ao lado do valor.

Uma maneira de evitar todos os efeitos colaterais é desativar a avaliação automática de funções (escolhendo **ferramentas** > **opções** > **depuração**  >  **Gerais**, em seguida, desmarcando **habilitar avaliação de propriedade e outras chamadas de função implícitas**).

Quando a avaliação de propriedades ou chamadas de função implícitas é desativada, você pode forçar a avaliação usando o **ac** modificador de formato (apenas para c#). Ver [especificadores em c# de formato](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Usar IDs de objeto na janela de inspeção (c# e Visual Basic)

Ocasionalmente, convém observar o comportamento de um objeto específico. Por exemplo, você talvez queira controlar um objeto referenciado por uma variável local depois que essa variável tiver saído do escopo. Em c# e Visual Basic, você pode criar IDs de objeto para instâncias específicas de tipos de referência e usá-los de **inspeção** janela e, em condições de ponto de interrupção. A ID de objeto é gerada pelo common language runtime (CLR) serviços de depuração e associada ao objeto.

> [!NOTE]
> IDs de objeto criar referências fracas que não impedem que o objeto que está sendo coletado como lixo. Eles só são válidos para a sessão de depuração atual.

No código a seguir, um método cria uma `Person` usando uma variável local, mas você deseja descobrir o que o `Person`do nome está em um método diferente:

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

Você pode adicionar uma referência a esse `Person` do objeto na **inspeção** janela da seguinte maneira:

1. Selecione uma linha no código que ocorre que o objeto foi criado.

2. Defina um ponto de interrupção (escolhendo **Debug** > **alternar ponto de interrupção** ou pressionando F9).

3. Inicie a depuração.

4. Quando a execução é interrompida no ponto de interrupção, abra o **Locals** janela (escolhendo **Debug** > **Windows** > **locais**), a variável com o botão direito e selecione **criar ID de objeto**.

   Você verá um sinal de cifrão (**$**) e a um número no **locais** janela, que é a ID de objeto.

   > [!NOTE]
   > Se você deseja ver as propriedades do objeto, como `Person.Name`, você deve habilitar a avaliação da propriedade escolhendo **ferramentas** > **opções**  >   **Depurando** > **geral**, em seguida, definindo **habilitar avaliação de propriedade e outras chamadas de função implícitas**.

5. Adicione a ID de objeto para o **Watch** janela clicando duas vezes o sinal de cifrão e o número e, em seguida, escolhendo **Adicionar inspeção**.

6. Defina um ponto de interrupção em que você deseja observar o comportamento do objeto.  No código anterior, que seria no `DoSomething()` método.

7. Continue a depuração. Quando a execução é interrompida na `DoSomething()` método, o **inspeção** janela exibe o `Person` objeto.

## <a name="use-registers-in-the-watch-window-c-only"></a>Usar registros na janela Watch (apenas C++)

Você pode adicionar nomes de registro e nomes de variáveis usando  **$ \<registrar&nbsp;nome >** ou  **@ \<registrar&nbsp;nome >** durante a depuração de código nativo. Para obter mais informações, consulte [pseudovariáveis](../debugger/pseudovariables.md).

## <a name="dynamic-view-and-the-watch-window"></a>Modo de exibição dinâmico e a janela Inspeção

Algumas linguagens de script (por exemplo, Python ou JavaScript) usam dinâmico ou [digitação pato](https://en.wikipedia.org/wiki/Duck_typing), e linguagens .NET (na versão 4.0 e posterior) dão suporte a objetos que são difíceis de observar usando janelas de depuração normais, porque eles pode ter métodos e propriedades de tempo de execução que não podem ser exibidos.

O **Watch** janela pode exibir um objeto dinâmico, que é criado de um tipo que implementa o <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Quando esse objeto é exibido, o depurador adiciona um especial **modo de exibição dinâmico** nó filho do nome do objeto, se você abrir o **Autos** janela (escolhendo **depurar**  >  **Windows** > **Autos**). Esse nó mostra os membros dinâmicos do objeto dinâmico, mas não permite a edição dos valores de membro.

Para inserir uma nova inspeção variável que converte um objeto em um objeto dinâmico:

1. Clique com botão direito qualquer filho de um **modo de exibição dinâmico**.
2. Escolher **Adicionar inspeção**. Em seguida `object.name` torna-se `((dynamic) object).name`.

Avaliar os membros de um **modo de exibição dinâmico** pode ter efeitos colaterais. Para obter uma explicação dos quais são os efeitos colaterais, consulte o [efeitos colaterais e expressões](#bkmk_sideEffects) seção. Para c#, o depurador não reavalia automaticamente os valores mostrados na **modo de exibição dinâmico** quando você depura em uma nova linha de código. Para o Visual Basic, as expressões adicionadas por meio de **modo de exibição dinâmico** são atualizados automaticamente.

Para obter instruções sobre como atualizar o **modo de exibição dinâmico** valores, consulte o [valores de inspeção de atualização que estão desatualizados](#bkmk_refreshWatch) seção.

Se você quiser exibir apenas a **modo de exibição dinâmico** para um objeto, você pode usar o **dinâmico** Formatar especificador no **Assista** janela:

- C#: `ObjectName, dynamic`
- Visual Basic: `$dynamic, ObjectName`

O **modo de exibição dinâmico** também melhora a experiência de depuração para objetos COM. Quando o depurador chega a um objeto COM encapsulado em **ComObject**, ele adiciona um **modo de exibição dinâmico** nó do objeto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observar uma única variável ou expressão com QuickWatch

Você pode usar o **QuickWatch** janela para observar uma única variável. Por exemplo, se você tiver o seguinte código:

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

Você pode observar uma variável na **QuickWatch** janela da seguinte maneira:

1. Defina um ponto de interrupção a `a = a + b;` linha.

2. Inicie a depuração. Interrompe a execução no ponto de interrupção.

3. Selecione a variável `a`.

4. Escolha **Debug** > **QuickWatch** ou pressione **Shift + F9**. O **QuickWatch** janela é exibida. No **valor** caixa, o `a` variável é mostrada com um valor de 1.

   ![Variável QuickWatch](../debugger/media/quickwatchvariable.png "QuickWatchVariable")

   Para avaliar uma expressão usando a variável, digite uma expressão como `a + b` para o **expressão** caixa e clique em **reavaliar**.

   ![Expressão QuickWatch](../debugger/media/quickwatchexpression.png "QuickWatchExpression")

   Para adicionar a variável ou expressão para o **Watch** janela a partir **QuickWatch**, escolha **Adicionar inspeção**.

   > [!NOTE]
   > O **QuickWatch** janela é uma janela de caixa de diálogo modal, portanto, você não pode continuar a depuração, desde que ele está aberto.

5. Fechar o **QuickWatch** janela. Agora você pode continuar a depuração enquanto você observar o valor de **inspeção** janela.

## <a name="see-also"></a>Consulte também

[Janelas do depurador](../debugger/debugger-windows.md)
