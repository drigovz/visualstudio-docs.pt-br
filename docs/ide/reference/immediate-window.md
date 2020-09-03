---
title: Janela imediata
ms.date: 02/25/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b21cdb9136abe1e960e5b74bbf09e7d1694519d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568952"
---
# <a name="immediate-window"></a>Janela Imediata

Use a janela **Imediato** para depurar e avaliar expressões, executar instruções e imprimir valores de variáveis. A janela **Imediato** avalia expressões compilando e usando o projeto atualmente selecionado.

Para exibir a janela **Imediato**, abra um projeto para edição, escolha **Depurar** > **Windows** > **Imediato** ou pressione **Ctrl**+**Alt**+**I**. Você também pode inserir **Debug.Immediate** na janela **Comando**.

A janela **Imediato** dá suporte ao IntelliSense.

## <a name="display-the-values-of-variables"></a>Exibir os valores de variáveis

A janela **Imediato** é particularmente útil quando você está depurando um aplicativo. Por exemplo, para verificar o valor de uma variável `varA`, use o [comando Imprimir](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

O ponto de interrogação (?) é um alias para `Debug.Print`, portanto, esse comando também pode ser escrito:

```cmd
? varA
```

As duas versões desse comando retornam o valor da variável `varA`.

> [!TIP]
> Para emitir um comando do Visual Studio na janela **Imediato**, você deve preceder o comando com um sinal de maior que (>). Para inserir vários comandos, alterne para a [janela Comando](command-window.md).

## <a name="design-time-expression-evaluation"></a>Avaliação de expressão de tempo de design

Você pode usar a janela **Imediato** para executar uma função ou sub-rotina em tempo de design.

### <a name="execute-a-function-at-design-time"></a>Executar uma função em tempo de design

1. Copie o seguinte código no aplicativo de console do Visual Basic:

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

2. No menu **Depuração**, escolha **Windows** > **Imediato**.

3. Digite `?MyFunction(2)` na janela **Imediato** e pressione **Enter**.

    A janela **Imediato** executa `MyFunction` e exibe `4`.

Se a função ou a sub-rotina contiverem um ponto de interrupção, o Visual Studio interromperá a execução no ponto apropriado. Então, você poderá usar o depurador do Windows para examinar o estado do programa. Para obter mais informações, consulte [Walkthrough: Depurando em tempo de design](../../debugger/walkthrough-debugging-at-design-time.md).

Não é possível usar a avaliação de expressão em tempo de design em tipos de projetos que exigem a inicialização de um ambiente de execução, incluindo projetos do Visual Studio Tools para Office, projetos Web, projetos de Dispositivo Inteligente e projetos do SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Avaliação de expressão em tempo de design em soluções multiprojeto

Ao estabelecer o contexto para a avaliação de expressão em tempo de design, o Visual Studio referencia o projeto atualmente selecionado no Gerenciador de Soluções. Se nenhum projeto estiver selecionado no Gerenciador de Soluções, o Visual Studio tentará avaliar a função com relação ao projeto de inicialização. Se a função não puder ser avaliada no contexto atual, você receberá uma mensagem de erro. Se você estiver tentando avaliar uma função em um projeto que não é o projeto de inicialização da solução e receber um erro, tente selecionar o projeto no Gerenciador de Soluções e tente fazer a avaliação novamente.

## <a name="enter-commands"></a>Inserir comandos

Você precisa inserir o sinal de maior que (>) ao emitir comandos do Visual Studio na janela **Imediato**. Use as teclas **Seta para cima** e **Seta para baixo** para rolar pelos comandos usados anteriormente.

|Tarefa|Solução|Exemplo|
|----------|--------------|-------------|
|Avaliar uma expressão.|Preceda a expressão com um ponto de interrogação (?).|`? a+b`|
|Entrar temporariamente no modo Comando enquanto está no modo Imediato (para executar um único comando).|Digite o comando precedendo-o com um sinal de maior que (>).|`>alias`|
|Mude para a janela Comando.|Digite `cmd` na janela, precedendo-o com um sinal de maior que (>).|`>cmd`|
|Mude para a janela Imediato.|Digite `immed` na janela, sem o sinal de maior que (>).|`immed`|

## <a name="mark-mode"></a>Modo de marca

Quando clica em qualquer linha anterior na janela **Imediato**, você muda automaticamente para o modo de Marca. Isso permite selecionar, editar e copiar o texto de comandos anteriores como você faria em qualquer editor de texto e colá-lo na linha atual.

## <a name="examples"></a>Exemplos

O exemplo a seguir mostra quatro expressões e seus resultados na janela **Imediato** para um projeto do Visual Basic.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>Notificações de exceção de primeira tentativa

Em algumas configurações, notificações de exceção de primeira tentativa são exibidas na janela **Imediato**.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Ativar ou desativar notificações de exceção de primeira tentativa na janela Imediato

1. No menu **Exibir**, clique em **Outras Janelas** e clique em **Saída**.

2. Clique com o botão direito do mouse na área de texto da Janela de **Saída** e marque ou desmarque **Mensagens de Exceção**.

## <a name="see-also"></a>Confira também

- [Navegar pelo Código com o Depurador](../../debugger/navigating-through-code-with-the-debugger.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Introdução ao depurador](../../debugger/debugger-feature-tour.md)
- [Walkthrough: Depurando em tempo de design](../../debugger/walkthrough-debugging-at-design-time.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Usando expressões regulares no Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
