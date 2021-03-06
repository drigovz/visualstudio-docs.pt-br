---
title: Informações de log com tracepoints | Microsoft Docs
description: Defina tracepoints para registrar informações para saída sem modificar ou parar seu código. Basta especificar uma cadeia de caracteres de saída na caixa de seleção ação nas configurações de ponto de interrupção.
ms.custom: SEO-VS-2020
ms.date: 10/28/2019
ms.topic: how-to
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 144f83b1be0c3a21aa5cb244f8498f61e3ef380a
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150087"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Informações de log para a janela de saída usando tracepoints no Visual Studio

Os Tracepoints permitem registrar informações na janela de saída em condições configuráveis sem modificar ou parar seu código. Esse recurso tem suporte para linguagens gerenciadas (C#, Visual Basic, F #) e código nativo, bem como para linguagens como JavaScript e Python.

## <a name="let39s-take-an-example"></a>Permitir que&#39;s Veja um exemplo

O programa de exemplo a seguir é um `for` loop simples com uma variável de contador que aumenta em uma cada vez que o loop executa outra iteração.

![Exemplo de contador](../debugger/media/counterexample.png "Exemplo de contador")

## <a name="set-tracepoints-in-source-code"></a>Definir tracepoints no código-fonte

Você pode definir tracepoints especificando uma cadeia de caracteres de saída na caixa de seleção **ação** na janela **configurações de ponto de interrupção** .

1. Para inicializar um tracepoint, primeiro clique na medianiz à esquerda do número de linha em que você deseja definir o tracepoint.

   ![Inicialização de ponto de interrupção](../debugger/media/breakpointinitialization.png "Inicialização de ponto de interrupção")

2. Passe o mouse sobre o círculo vermelho e clique no ícone de engrenagem.
3. Isso abre a janela **configurações de ponto de interrupção** .

   ![Janela de ponto de interrupção](../debugger/media/breakpointwindow.png "Janela de ponto de interrupção")

4. Marque a caixa de seleção **ação** .

   ![Caixa de ações verificadas](../debugger/media/checkedactionsbox.png "Caixa de ações verificadas")

   Observe como o círculo vermelho muda para um losango indicando que você mudou de um ponto de interrupção para o tracepoint.

5. Insira a mensagem que você deseja fazer logon na caixa de texto **mostrar uma mensagem na janela de saída** (para obter detalhes, consulte as seções posteriores neste artigo).

   O tracepoint agora está definido. Pressione o &quot; &quot; botão fechar se tudo o que você deseja fazer é registrar algumas informações no janela de saída.

6. Se você quiser adicionar condições que determinam se a mensagem é exibida, marque a caixa de seleção **condições** .

   ![Caixa condições verificadas](../debugger/media/checkedconditionsbox.png "Caixa condições verificadas")

   Você tem três opções de condições: **expressão condicional**, **filtro** e **contagem de acesso**.

## <a name="actions-menu"></a>Menu de ações

Esse menu permite que você registre uma mensagem na janela de saída. Digite as cadeias de caracteres que você deseja gerar na caixa de mensagem (não há aspas necessárias). Se você quiser exibir valores de variáveis, certifique-se de colocá-los entre chaves.

Por exemplo, se você quiser exibir o valor da `counter` variável no console de saída, digite {Counter} na caixa de texto da mensagem.

![Mensagem de saída do contador](../debugger/media/counteroutputmessage.png "Mensagem de saída do contador")

Se você clicar em **fechar** e depurar o programa (**F5**), você verá a seguinte saída na janela saída.

![Mensagem de ações em Janela de Saída](../debugger/media/actionsmessageinoutputwindow.png "Mensagem de ações em Janela de Saída")

Você também pode usar palavras-chave especiais para exibir informações mais específicas. Insira a palavra-chave exatamente como mostrado abaixo (use um "$" na frente de cada palavra-chave e todas as maiúsculas para a palavra-chave em si).

| Palavra-chave | O que é exibido |
| --- | --- |
| $ADDRESS | Instrução atual |
| $CALLER | Nome da função de chamada |
| $CALLSTACK | Pilha de chamadas |
| $FUNCTION | Nome da função atual |
| $PID | ID do Processo |
| $PNAME | Nome do processo |
| $TID | ID do thread |
| $TNAME   | Nome do thread |
| $TICK | Contagem de tiques (do Windows ObterContagemMarcaEscala) |

## <a name="conditions-menu"></a>Menu de condições

As condições permitem filtrar as mensagens de saída, para que elas sejam exibidas somente em determinados cenários. Há três tipos principais de condições disponíveis para você.

### <a name="conditional-expression"></a>Expressões condicionais
Para uma expressão condicional, uma mensagem de saída é exibida somente quando determinadas condições são atendidas.

Para expressões condicionais, você pode definir o tracepoint para gerar uma mensagem quando uma determinada condição for verdadeira ou quando ela for alterada. Por exemplo, se você quiser apenas exibir o valor do contador durante iterações iguais do `for` loop, você poderá selecionar a opção **é verdadeiro** e digitar `i%2 == 0` a caixa de texto da mensagem.

![A expressão condicional é verdadeira](../debugger/media/conditionalexpressionistrue.png "A expressão condicional é verdadeira")

Se você quiser imprimir o valor do contador quando a iteração do `for` loop for alterada, selecione a opção **quando alterado** e digite `i` na caixa de texto da mensagem.

![Expressão condicional quando alterada](../debugger/media/conditionalexpressionwhenchanged.png "Expressão condicional quando alterada")

O comportamento da opção  **quando alterado**  é diferente para linguagens de programação diferentes.

- Para código nativo, o depurador não considera a primeira avaliação da condição como uma alteração, portanto, não atinge o tracepoint na primeira avaliação.
- Para código gerenciado, o depurador atinge o tracepoint na primeira avaliação depois **que a alteração**  é selecionada.

Para obter uma visão mais abrangente das expressões válidas que você pode usar ao definir condições, consulte [expressões no depurador](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Contagem de acesso
Uma condição de contagem de ocorrências permite que você envie a saída somente depois que a linha de código em que o tracepoint está definido tiver executado um número especificado de vezes.

Para contagem de ocorrências, você pode optar por gerar uma mensagem quando a linha de código onde o tracepoint está definido tiver sido executada várias vezes que é igual a, é um múltiplo ou maior ou igual ao valor especificado da contagem de ocorrências. Escolha a opção mais adequada às suas necessidades e digite um valor inteiro no campo (por exemplo, 5) que represente essa iteração de interesse.

![Contagem de acesso à expressão condicional](../debugger/media/conditionalexpressionhitcount.png "Contagem de acesso à expressão condicional")

### <a name="filter"></a>Filtrar
Para uma condição de filtro, especifique quais dispositivos, processos ou saída de threads são mostrados para.

![Filtro de expressão condicional](../debugger/media/conditionalexpressionfilter.png "Filtro de expressão condicional")

Lista de expressões de filtro:

- MachineName = "nome"
- ProcessId = valor
- ProcessName = "nome"
- ThreadId = valor
- ThreadName = "nome"

Coloque as cadeias de caracteres (como nomes) entre aspas duplas. Os valores podem ser inseridos sem aspas. Você pode combinar cláusulas usando `&` ( `AND` ), `||` ( `OR` ), `!` ( `NOT` ), entre parênteses.

## <a name="considerations"></a>Considerações

Embora os tracepoints destinam-se a tornar a depuração uma experiência mais limpa e mais suave, há algumas considerações que você deve conhecer quando se trata de usá-las.

Às vezes, quando você inspeciona uma propriedade ou atributo de um objeto, seu valor pode ser alterado. Se o valor for alterado durante a inspeção, não será um bug causado pelo próprio recurso tracepoint. No entanto, o uso de tracepoints para inspecionar objetos não evita essas modificações acidentais.

A maneira como as expressões são avaliadas na caixa de mensagem de **ação** pode ser diferente da linguagem que você está usando no momento para desenvolvimento. Por exemplo, para gerar uma cadeia de caracteres, não é necessário encapsular uma mensagem entre aspas mesmo que você normalmente use `Debug.WriteLine()` ou `console.log()` . Além disso, a sintaxe de chave ( `{ }` ) para expressões de saída também pode ser diferente da Convenção de saída de valores em sua linguagem de desenvolvimento. (No entanto, o conteúdo dentro das chaves ( `{ }` ) ainda deve ser escrito usando a sintaxe da linguagem de desenvolvimento.

Se você estiver tentando depurar um aplicativo ao vivo e procurando um recurso semelhante, confira nosso recurso logpoint na Depurador de Instantâneos. O depurador de instantâneo é uma ferramenta usada para investigar problemas em aplicativos de produção. O Logpoints também permite que você envie mensagens para o Janela de Saída sem precisar modificar o código-fonte e não afete o aplicativo em execução. Para obter mais informações, consulte [Depurar aplicativo dinâmico do Azure](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Confira também

- [O que é depuração?](../debugger/what-is-debugging.md)
- [Escreva um código C# melhor usando o Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Primeira olhada na depuração](../debugger/debugger-feature-tour.md)
- [Expressões no depurador](expressions-in-the-debugger.md)
- [Usar pontos de interrupção](../debugger/using-breakpoints.md)
- [Depurar aplicativos dinâmicos do Azure](../debugger/debug-live-azure-applications.md)
