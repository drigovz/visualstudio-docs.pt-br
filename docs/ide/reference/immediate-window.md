---
title: Janela imediata
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91f25f9ab44bee749283603b78744c9e01e4e469
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992627"
---
# <a name="immediate-window"></a>Janela Imediata

A janela **Imediato** é usada para depurar e avaliar expressões, executar instruções, imprimir valores de variáveis e assim por diante. Ela permite inserir expressões a serem avaliadas ou executadas pela linguagem de desenvolvimento durante a depuração.

Para exibir a janela **Imediato**, abra um projeto para edição, escolha **Depurar** > **Windows** > **Imediato** ou pressione **Ctrl**+**Alt**+**I**. Você também pode inserir **Debug.Immediate** na janela **Comando**.

Você pode usar a janela **Imediato** para emitir comandos individuais do Visual Studio. Os comandos disponíveis incluem `EvaluateStatement`, que pode ser usado para atribuir valores a variáveis. A janela **Imediato** também dá suporte ao IntelliSense.

## <a name="display-the-values-of-variables"></a>Exibir os valores de variáveis

A janela **Imediato** pode ser particularmente útil ao depurar um aplicativo. Por exemplo, para verificar o valor de uma variável `varA`, você pode usar o [Comando Imprimir](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

O ponto de interrogação (?) é um alias para `Debug.Print`, portanto, esse comando também pode ser escrito:

```cmd
>? varA
```

As duas versões desse comando retornam o valor da variável `varA`.

> [!TIP]
> Para emitir um comando do Visual Studio na janela **Imediato**, você deve preceder o comando com um sinal de maior que (>). Para inserir vários comandos, mude para a janela **Comando**.

## <a name="design-time-expression-evaluation"></a>Avaliação de expressão de tempo de design

Você pode usar a janela **Imediato** para executar uma função ou sub-rotina em tempo de design.

### <a name="execute-a-function-at-design-time"></a>Executar uma função em tempo de design

1. Copie o código a seguir em um aplicativo de console do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. No menu **Depurar**, clique em **Janelas** e clique em **Imediato**.

3. Digite `?MyFunction(2)` na janela **Imediato** e pressione **Enter**.

    A janela **Imediato** executa `MyFunction` e exibe `4`.

Se a função ou a sub-rotina contiverem um ponto de interrupção, o Visual Studio interromperá a execução no ponto apropriado. Então, você poderá usar o depurador do Windows para examinar o estado do programa. Para obter mais informações, confira [Passo a passo: Depuração em tempo de design](../../debugger/walkthrough-debugging-at-design-time.md).

Não é possível usar a avaliação de expressão em tempo de design em tipos de projetos que exigem a inicialização de um ambiente de execução, incluindo projetos [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)], projetos Web, projetos de dispositivo inteligente e projetos SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Avaliação de expressão em tempo de design em soluções multiprojeto

Ao estabelecer o contexto para a avaliação de expressão em tempo de design, o Visual Studio faz referência ao projeto selecionado atualmente no Gerenciador de Soluções. Se nenhum projeto estiver selecionado no Gerenciador de Soluções, o Visual Studio tentará avaliar a função com relação ao projeto de inicialização. Se a função não puder ser avaliada no contexto atual, você receberá uma mensagem de erro. Se você estiver tentando avaliar uma função em um projeto que não é o projeto de inicialização da solução e receber um erro, tente selecionar o projeto no Gerenciador de Soluções e tente avaliar novamente.

## <a name="enter-commands"></a>Inserir comandos

Você precisa inserir o sinal de maior que (>) ao emitir comandos do Visual Studio na janela **Imediato**. Use as teclas de **seta para cima** e **seta para baixo** para rolar pelos comandos emitidos anteriormente.

|Tarefa|Solução|Exemplo|
|----------|--------------|-------------|
|Avaliar uma expressão.|Preceda a expressão com um ponto de interrogação (?).|`? a+b`|
|Entrar temporariamente no modo Comando enquanto está no modo Imediato (para executar um único comando).|Digite o comando precedendo-o com um sinal de maior que (>).|`>alias`|
|Mude para a janela Comando.|Digite `cmd` na janela, precedendo-o com um sinal de maior que (>).|`>cmd`|
|Mude para a janela Imediato.|Digite `immed` na janela, sem o sinal de maior que (>).|`immed`|

## <a name="mark-mode"></a>Modo de marca

Quando clica em qualquer linha anterior na janela **Imediato**, você muda automaticamente para o modo de Marca. Isso permite selecionar, editar e copiar o texto de comandos anteriores como você faria em qualquer editor de texto e colá-lo na linha atual.

## <a name="the-equals-sign"></a>O sinal de igual (=)

A janela usada para inserir o comando `EvaluateStatement` determina se um sinal de igual (=) é interpretado como um operador de comparação ou um operador de atribuição.

Na janela **Imediato**, um sinal de igual (=) é interpretado como um operador de atribuição. Assim, por exemplo, o comando

```cmd
>Debug.EvaluateStatement(varA=varB)
```

atribui o valor da variável `varB` à variável `varA`.

Na janela **Comando**, por outro lado, o sinal de igual (=) é interpretado como um operador de comparação. Você não pode usar operações de atribuição na janela **Comando**. Dessa forma, por exemplo, se os valores das variáveis `varA` e `varB` forem diferentes, o comando

```cmd
>Debug.EvaluateStatement(varA=varB)
```

retorna um valor de `False`.

## <a name="first-chance-exception-notifications"></a>Notificações de exceção de primeira tentativa

Em algumas configurações, notificações de exceção de primeira tentativa são exibidas na janela **Imediato**.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Ativar ou desativar notificações de exceção de primeira tentativa na janela Imediato

1. No menu **Exibir**, clique em **Outras Janelas** e clique em **Saída**.

2. Clique com o botão direito do mouse na área de texto da Janela de **Saída** e marque ou desmarque **Mensagens de Exceção**.

## <a name="see-also"></a>Consulte também

- [Navegar pelo Código com o Depurador](../../debugger/navigating-through-code-with-the-debugger.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Introdução ao depurador](../../debugger/debugger-feature-tour.md)
- [Passo a passo: Depuração em tempo de design](../../debugger/walkthrough-debugging-at-design-time.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Usando expressões regulares no Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
