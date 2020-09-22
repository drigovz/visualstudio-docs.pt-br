---
title: Janelas Watch e QuickWatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3f79e492440f98f733488afb241fa6f86e220b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838271"
---
# <a name="watch-and-quickwatch-windows"></a>Janelas de Inspeção e QuickWatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar a **inspeção** (**depuração/Windows/inspeção/inspeção (1, 2, 3, 4)**) e **QuickWatch** (clique com o botão direito do mouse em Variable/ **debug/QuickWatch**) Windows para inspecionar variáveis e expressões durante uma sessão de depuração.  A diferença é que a janela **Watch** pode exibir várias variáveis, enquanto a janela **QuickWatch** exibe uma única variável por vez.  
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Observando uma única variável com QuickWatch  
 Você pode usar a janela **QuickWatch** para observar uma única variável. Por exemplo, se você tiver o seguinte código:  
  
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
  
 Você pode observar a variável na janela QuickWatch da seguinte maneira:  
  
1. Defina um ponto de interrupção na linha `a = a + b;`.  
  
2. Inicie a depuração. A execução é interrompida no ponto de interrupção.  
  
3. Abra a janela **QuickWatch** (clique com o botão direito do mouse em a, escolha **debug/QuickWatch**ou **Shift + F9**). Você pode abrir a janela e adicionar uma variável à janela **expressão** e, em seguida, clicar em **reavaliar**. Você deve ver a variável na janela **valores** , com um valor de 2.  
  
4. A janela **QuickWatch** é uma janela de diálogo modal, portanto você não pode continuar a depuração enquanto ela estiver aberta. Você pode adicionar a variável à janela de **inspeção** clicando em **Adicionar inspeção**.  
  
5. Feche a janela **QuickWatch** . Agora você pode continuar a depuração enquanto observa o valor na janela **Watch**  
  
## <a name="observing-variables-with-the-watch-window"></a>Observando variáveis com o janela Inspeção  
 Você pode observar várias variáveis com a janela **Watch** . Por exemplo, se você tiver o seguinte código:  
  
```csharp  
static void Main(string[] args)  
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
}  
  
```  
  
 Adicione os valores das três variáveis ao janela Inspeção da seguinte maneira:  
  
1. Defina um ponto de interrupção na linha `c = a + b;`.  
  
2. Iniciar Depuração (**F5**). A execução é interrompida no ponto de interrupção.  
  
3. Abra o janela Inspeção (**debug/Windows/Watch/Watch 1**ou **Ctrl + Alt + W, 1**).  
  
4. Adicione a `a` variável à primeira linha, a `b` variável à segunda linha e a `c` variável à terceira linha.  
  
5. Continue a depuração.  
  
   Você deve ver os valores de variáveis mudando conforme você itera pelo `for` loop.  
  
   Se você estiver programando em código nativo, às vezes talvez seja necessário qualificar o contexto de um nome de variável ou de uma expressão que contenham um nome de variável. O contexto é a função, o arquivo de origem e o módulo em que uma variável está localizada. Se você precisar fazer isso, poderá usar a sintaxe de operador de contexto. Para obter mais informações, consulte expressões em C++.  
  
## <a name="observing-expressions-with-the-watch-window"></a>Observando expressões com o janela Inspeção  
 Agora, vamos tentar usar uma expressão. Você pode adicionar qualquer expressão válida reconhecida pelo depurador.  
  
 Por exemplo, se você tiver o código listado na seção anterior, poderá obter a média dos três valores como este:  
  
 ![Inspeção de variáveis](../debugger/media/watchexpression.png "Inspeção de variáveis")  
  
 Em geral, as regras para avaliar expressões na janela **Watch** são as mesmas que as regras para avaliar expressões em sua linguagem de codificação. Se a expressão tiver um erro de sintaxe, você poderá esperar o mesmo erro do compilador que veria no editor de código. Aqui está um exemplo:  
  
 ![WatchExpressionError](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
## <a name="refreshing-watch-values-that-are-out-of-date"></a><a name="bkmk_refreshWatch"></a> Atualizando valores de inspeção que estão desatualizados  
 Em determinadas circunstâncias, você pode ver um ícone de atualização (um círculo com duas setas ou um círculo com duas linhas onduladas) quando uma expressão é avaliada na janela **Watch** .  Por exemplo, se você tiver a avaliação de propriedade desativada (**ferramentas/opções/depuração/habilitar avaliação de propriedade e outras chamadas de função implícitas**), e você tiver o seguinte código:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Se você definir uma inspeção na `Count` propriedade da lista, deverá ver algo semelhante ao seguinte:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Isso indica um erro ou um valor que está desatualizado. Geralmente, você pode atualizar o valor clicando no ícone, mas, em alguns casos, você pode preferir não atualizá-lo. Primeiro, você precisa saber por que o valor não foi avaliado.  
  
 Se você apontar para o ícone, uma dica de ferramenta fornecerá informações sobre como a expressão não foi avaliada.  Se as setas de circundamento aparecerem, isso significará que a expressão não foi avaliada para um dos seguintes motivos:  
  
- • Ocorreu um erro porque a expressão estava sendo avaliada. Por exemplo, um tempo limite pode ter ocorrido, ou uma variável pode ter ficado fora do escopo.  
  
- • A expressão contém uma chamada de função que pode disparar um efeito colateral no aplicativo (consulte [efeitos colaterais e expressões](#bkmk_sideEffects)).  
  
- A avaliação automática de propriedades e chamadas de funções implícitas pelo depurador é desativada (**ferramentas/opções/depuração/habilita a avaliação de propriedade e outras chamadas de função implícitas**) e, em seguida, a expressão não pode ser avaliada automaticamente.  
  
  Para atualizar o valor, clique no ícone atualizar ou pressione a barra de espaços. O depurador tentará reavaliar a expressão. Se o ícone de atualização apareceu porque a avaliação automática das propriedades e dos efeitos colaterais implícitos foi desativada, a expressão pode ser avaliada.  
  
  Se você vir um ícone que é um círculo com duas linhas onduladas que se assemelham a threads, a expressão não foi avaliada devido a uma possível dependência entre threads. Em outras palavras, avaliar o código requer que outros threads em seu aplicativo sejam executados temporariamente. Quando você está no modo de interrupção, todos os threads em seu aplicativo normalmente estão parados. Permitir que outros threads sejam executados temporariamente pode ter efeitos inesperados sobre o estado do seu programa e faz com que o depurador ignore eventos como pontos de interrupção e exceções geradas nesses threads.  
  
## <a name="side-effects-and-expressions"></a><a name="bkmk_sideEffects"></a> Efeitos colaterais e expressões  
 Avaliar algumas expressões pode alterar o valor de uma variável ou, de outra forma, afetar o estado do programa. Por exemplo, avaliar a expressão a seguir altera o valor de `var1`:  
  
```  
var1 = var2  
```  
  
 Isso é chamado de [efeito colateral](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Os efeitos colaterais podem tornar a depuração mais difícil, alterando a maneira como seu programa funciona.  
  
 Uma expressão que é conhecida por ter efeitos colaterais é avaliada apenas uma vez, quando você a insere primeiro. As avaliações subsequentes serão desativadas. Você pode substituir manualmente esse comportamento clicando no ícone de atualização que aparece ao lado do valor.  
  
 Uma maneira de evitar todos os efeitos colaterais é desativar a avaliação de função automática (**ferramentas/opções/depuração/habilitar a avaliação de propriedade e outras chamadas de função implícitas**).  
  
 Quando a avaliação de propriedades ou chamadas de função implícitas está desativada, você pode forçar a avaliação usando o modificador de formato **AC** (somente para C#). Consulte [especificadores de formato em C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="using-object-ids-in-the-watch-window-c-and-visual-basic"></a>Usando IDs de objeto no janela Inspeção (C# e Visual Basic)  
 Há ocasiões em que você deseja observar o comportamento de um objeto específico; por exemplo, talvez você queira acompanhar um objeto referido por uma variável local depois que essa variável sair do escopo. Em C# e Visual Basic, você pode criar IDs de objeto para instâncias específicas de tipos de referência e usá-las no janela Inspeção e em condições de ponto de interrupção. A ID de objeto é gerada pelos serviços de depuração de Common Language Runtime (CLR) e associada ao objeto.  
  
> [!NOTE]
> As IDs de objeto criam referências fracas e não impedem que o objeto seja coletado como lixo. Eles são válidos somente para a sessão de depuração atual.  
  
 No código a seguir, um método cria um `Person` usando uma variável local, mas você deseja descobrir qual é o `Person` nome de um método diferente:  
  
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
    List<Person> _people = new List<Person>();  
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
  
 Você pode adicionar uma referência a esse `Person` objeto na janela **Watch** da seguinte maneira:  
  
1. Defina um ponto de interrupção no código uma vez após o objeto ter sido criado.  
  
2. Inicie a depuração e quando a execução for interrompida no ponto de interrupção, localize a variável na janela **locais** , clique com o botão direito do mouse nela e selecione **criar ID de objeto**.  
  
3. Você deve ver **$** mais um número na janela **locais** . Esta é a ID do objeto.  
  
4. Adicione a ID de objeto ao janela Inspeção.  
  
5. Defina um ponto de interrupção onde você deseja observar o comportamento do objeto.  No código acima, isso estaria no `DoSomething()` método.  
  
6. Continuar a depuração e quando a execução for interrompida no `DoSomething()` método, a janela de **Observação** exibirá o `Person` objeto.  
  
> [!NOTE]
> Se você quiser ver as propriedades do objeto, como `Person.Name` no exemplo acima, você deve ter habilitado a avaliação de propriedade.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Usando registros no janela Inspeção (somente C++)  
 Se você estiver depurando código nativo, poderá adicionar nomes de registro, bem como nomes de variáveis usando **$\<register name>** ou **@\<register name>** .  Para obter mais informações, consulte [Pseudovariables](../debugger/pseudovariables.md).  
  
## <a name="dynamicview-and-the-watch-window"></a>DynamicView e o janela Inspeção  
 Algumas linguagens de script (por exemplo, JavaScript ou Python) usam tipos dinâmicos ou [patos](https://en.wikipedia.org/wiki/Duck_typing), e as linguagens .net (na versão 4,0 e posteriores) oferecem suporte a objetos que são difíceis de observar usando as janelas de depuração normais, pois podem ter propriedades e métodos de tempo de execução que não podem ser exibidos.  
  
 Quando o janela Inspeção exibe um ou um objeto criado com base em um tipo que implementa o <xref:System.Dynamic.IDynamicMetaObjectProvider> , o depurador adiciona um nó de **exibição dinâmica**  especial à exibição **automática** . Esse nó mostra os membros dinâmicos do objeto dinâmico, mas não permite a edição dos valores de membro.  
  
 Se você clicar com o botão direito do mouse em qualquer filho de uma **exibição dinâmica** e escolher **Adicionar inspeção**, o depurador inserirá uma nova variável Watch que converterá um objeto em um objeto dinâmico. Em outras palavras, o **nome do objeto** se torna (**objeto (dinâmico)). Nome**.  
  
 Avaliar os membros de um **modo de exibição dinâmico** pode ter efeitos colaterais. Para obter uma explicação sobre quais são os efeitos colaterais, consulte [efeitos colaterais e expressões](#bkmk_sideEffects). Para o C#, o depurador não reavalia automaticamente os valores mostrados na **exibição dinâmica** ao passar para uma nova linha de código. Por Visual Basic, as expressões adicionadas por meio da **exibição dinâmica** são atualizadas automaticamente.  
  
 Para obter instruções sobre como atualizar os valores de exibição dinâmica, consulte [atualizando valores de inspeção que estão desatualizados](#bkmk_refreshWatch).  
  
 Se você quiser exibir apenas a **exibição dinâmica** de um objeto, poderá usar o especificador de formato **dinâmico** :  
  
- C#: **objectname, dinâmico**  
  
- Visual Basic:: **$Dynamic, ObjectName**  
  
  A **exibição dinâmica** também aprimora a experiência de depuração para objetos com. Quando o depurador encontra um objeto COM encapsulado em **System. __ComObject**, ele adiciona um nó de **exibição dinâmica** para o objeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Janelas do depurador](../debugger/debugger-windows.md)
