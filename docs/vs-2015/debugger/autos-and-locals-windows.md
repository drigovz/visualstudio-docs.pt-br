---
title: Janelas automáticas e locais | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 261c0c0bd8b48634c8d24d56ee4df7ea3bbcf135
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161711"
---
# <a name="autos-and-locals-windows"></a>Janelas autos e locais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A **janela Autos** (durante a depuração, **Ctrl + Alt + V, A**ou **debug/Windows/autoies**) e a janela **locais** (durante a depuração, **Ctrl + Alt + V, L**ou **debug/Windows/locals**) são bastante úteis quando você deseja ver valores de variáveis enquanto estiver depurando. A janela **locais** exibe as variáveis que são definidas no escopo local, que geralmente é a função ou o método que está sendo executado no momento. A janela **automáticos** exibe as variáveis usadas em torno da linha atual (o local onde o depurador é interrompido). Exatamente quais variáveis são exibidas em diferentes idiomas. Ver quais variáveis aparecem na janela de automóveis? acima.  
  
 Se você precisar de mais informações sobre a depuração básica, consulte [introdução com o depurador](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Examinando objetos nas janelas automáticas e locais  
 Matrizes e objetos são exibidos nas janelas automáticos e locais como controles de árvore. Clique na seta à esquerda do nome da variável para expandir a exibição para mostrar campos e propriedades. Aqui está um exemplo de uma <xref:System.IO.FileStream> do objeto na janela **Locals**:  
  
 ![Locais&#45;FileStream](../debugger/media/locals-filestream.png "Locais-FileStream")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Quais variáveis aparecem na janela de automóveis?  
 Você pode usar a janela **autos** em C#, Visual Basic e código C++. A janela **autos** não dá suporte a JavaScript ou F #.  
  
 Em C# e Visual Basic, a janela **autos** exibe qualquer variável usada na linha atual ou anterior. Por exemplo, se você declarar quatro variáveis e defini-las da seguinte maneira:  
  
```csharp  
public static void Main()  
{  
    int a, b, c, d;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
}  
```  
  
 Se você definir um ponto de interrupção na linha `c = 3` ; e executar o depurador, quando a execução parar, a janela **autos** terá a seguinte aparência:  
  
 ![Auto&#45;CSharp](../debugger/media/autos-csharp.png "Auto-CSharp")  
  
 Observe que o valor de `c` é 0, porque a linha `c = 3` ainda não foi executada.  
  
 Em C++, a janela **autos** exibe as variáveis usadas pelo menos três linhas antes da linha atual (a linha na qual a execução é interrompida). Se você declarar seis variáveis:  
  
```cpp  
void main() {  
    int a, b, c, d, e, f;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
    e = 5;  
    f = 6;  
}  
```  
  
 Se você definir um ponto de interrupção na linha `e = 5;` e executar o depurador, quando a execução parar, a janela **automáticos** terá a seguinte aparência:  
  
 ![Auto&#45;Cplus](../debugger/media/autos-cplus.png "Auto-Cplus")  
  
 Observe que a variável e não foi inicializada porque o código na linha `e = 5;` ainda não foi executado.  
  
 Você também pode ver os valores de retorno de funções e métodos em determinadas circunstâncias. Consulte [Exibir valores de retorno das chamadas de método](#bkmk_returnValue) abaixo.  
  
## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Exibir valores de retorno de chamadas de método  
 No código .NET e C++, você pode examinar valores de retorno ao passar ou sair de uma chamada de método. Essa funcionalidade é útil quando o resultado de uma chamada de método não é armazenado em uma variável local, por exemplo, quando um método é usado como um parâmetro ou como um valor de retorno de outro método.  
  
 O código C# a seguir adiciona os valores de retorno de duas funções:  
  
```csharp  
static void Main(string[] args)  
{  
    int a, b, c, d;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
    int x = sumVars(a, b) + subtractVars(c, d);  
}  
  
private static int sumVars(int i, int j)  
{  
    return i + j;  
}  
  
private static int subtractVars(int i, int j)  
{  
    return j - i;  
}  
  
```  
  
 Defina um ponto de interrupção na `x = sumVars(a, b) + subtractVars(c, d);` linha int.  
  
 Inicie a depuração e quando a execução for interrompida no primeiro ponto de interrupção, pressione **F10 (depuração)**. Você deve ver o seguinte na janela de **automóveis** :  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Por que os valores de variáveis às vezes são vermelhos em locais e as janelas automáticas?  
 Você pode observar que o valor de uma variável, às vezes, é vermelho nas janelas **locais** e **automáticas** . Esses são valores de variáveis que foram alterados desde a última avaliação. A alteração pode ser de uma sessão de depuração anterior ou porque o valor foi alterado na janela.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Alterando o formato numérico de uma janela variável  
 O formato numérico padrão é decimal, mas você pode alterá-lo para hexadecimal. Clique com o botão direito do mouse dentro de uma janela **locais** ou **automáticos** e selecione **exibição hexadecimal**. A alteração afeta todas as janelas do depurador.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Editando um valor em uma janela variável  
 Você pode editar os valores da maioria das variáveis que aparecem nas janelas **automáticos**, **locais**, **inspecionar**e **QuickWatch** . Para obter informações sobre as janelas **Watch** e **QuickWatch** , consulte as [janelas Watch e QuickWatch](../debugger/watch-and-quickwatch-windows.md). Basta clicar duas vezes no valor que você deseja alterar e adicionar o novo valor.  
  
 Você pode inserir uma expressão para um valor, por exemplo `a + b` . O depurador aceita mais expressões de linguagem válidas.  
  
 No código C++ nativo, talvez você precise qualificar o contexto de um nome de variável. Para obter mais informações, consulte [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
 No entanto, você deve ter cuidado ao alterar valores. Estes são alguns problemas possíveis:  
  
- Avaliar algumas expressões pode alterar o valor de uma variável ou, de outra forma, afetar o estado do programa. Por exemplo, avaliar `var1 = ++var2` altera o valor de `var1` e `var2` .  
  
     As expressões que alteram dados devem ter [efeitos colaterais](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), o que pode produzir resultados inesperados se você não estiver ciente deles. Certifique-se de entender as consequências de tal alteração antes de fazê-lo.  
  
- Editar valores de ponto flutuante pode resultar em imprecisões secundárias devido à conversão decimal-binária de componentes fracionários. Mesmo uma edição aparentemente inofensiva pode resultar em alterações em alguns bits menos significativos na variável de ponto flutuante.  
  
## <a name="debug-location-toolbar"></a>Depurar barra de ferramentas de local  
 Você pode usar a barra de ferramentas **local de depuração** para selecionar a função, o thread ou o processo desejado. Definir um ponto de interrupção e iniciar a depuração. (Se você não vir essa barra de ferramentas, poderá habilitá-la clicando em uma parte vazia da área da barra de ferramentas. Você deve ver uma lista de barras de ferramentas; Selecione o **local de depuração**). Quando o ponto de interrupção é atingido, a execução é interrompida e você pode ver a barra de ferramentas local de depuração, que é a linha inferior do gráfico a seguir:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Você também pode alterar o contexto para diferentes chamadas de função, threads ou processos clicando duas vezes no elemento na janela **pilha de chamadas** , na janela **threads** ou na janela **processos** .  
  
## <a name="see-also"></a>Consulte Também  
 [Janelas do depurador](../debugger/debugger-windows.md)
