---
title: Comandos do console do JavaScript | Microsoft Docs
description: Use comandos para enviar mensagens e realizar outras tarefas na janela do console do JavaScript. Este artigo se aplica a aplicativos Node.js, aplicativos UWP e Apache Cordova aplicativos.
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.topic: reference
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- uwp
- cordova
ms.openlocfilehash: d874b2831d906a42856e71d42dac6df1a1fe8d6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906376"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Comandos do console do JavaScript no Visual Studio

Você pode usar comandos para enviar mensagens e executar outras tarefas na janela Console do JavaScript do Visual Studio. Para obter exemplos que mostram como usar essa janela, consulte [início rápido: Depurar JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017&preserve-view=true). As informações neste tópico aplicam-se a Node.js aplicativo, aplicativos UWP e aplicativos criados usando Ferramentas do Visual Studio para Apache Cordova.

Se a janela do console do JavaScript estiver fechada, você poderá abri-la enquanto estiver depurando no Visual Studio escolhendo **depurar**  >  console do **Windows**  >  **JavaScript**.

> [!NOTE]
> Se a janela não estiver disponível durante uma sessão de depuração, verifique se o tipo de depurador está definido para **Script** nas propriedades de depuração do projeto.

Para obter informações sobre como usar o console do em ferramentas de desenvolvedor do Microsoft Edge, consulte [Este tópico](/microsoft-edge/devtools-guide).

## <a name="console-object-commands"></a>Comandos do objeto console

Esta tabela mostra a sintaxe dos comandos de objeto do `console` que você pode usar na janela do Console do JavaScript ou para enviar mensagens de seu código para o console. Esse objeto oferece diversos formatos para que você possa distinguir entre mensagens informativas e mensagens de erro, se desejar.

Você pode usar o formato de comando mais longo, `window.console.[command]`, se precisar evitar uma possível confusão com objetos locais chamados console.

> [!TIP]
> Nas versões anteriores do Visual Studio não há suporte para o conjunto completo de comandos. Use o IntelliSense no objeto de console para obter informações rápidas sobre comandos com suporte.

|Comando|Descrição|Exemplo|
|-------------|-----------------|-------------|
|`assert(expression, message)`|Envia uma mensagem quando `expression` é avaliado como **falso**.|`console.assert((x == 1), "assert message: x != 1");`|
|`clear()`|Limpa as mensagens da janela do console, incluindo mensagens de erro de script, e limpa também o script exibido na janela do console. Não limpa o script inserido no prompt de entrada do console.|`console.clear();`|
|`count(title)`|Envia o número de vezes que o comando count foi chamado para a janela do console. Cada chamada do comando count é identificada exclusivamente pelo `title`opcional.<br /><br /> A entrada existente na janela do console é identificada pelo parâmetro `title` (se presente) e atualizada pelo comando count. Não é criada uma nova entrada.|`console.count();`<br /><br /> `console.count("inner loop");`|
|`debug(message)`|Envia `message` para a janela do console.<br /><br /> Esse comando é idêntico a console.log.<br /><br /> Os objetos transmitidos usando o comando são convertidos em um valor de cadeia de caracteres.|`console.debug("logging message");`|
|`dir(object)`|Envia o objeto especificado para a janela do console e o exibe em um visualizador de objetos. Você pode usar o visualizador para inspecionar propriedades na janela do console.|`console.dir(obj);`|
|`dirxml(object)`|Envia o nó XML `object` especificado para a janela do console e o exibe como uma árvore de nós XML.|`console.dirxaml(xmlNode);`|
|`error(message)`|Envia `message` para a janela do console. O texto da mensagem está em vermelho e antecedido por um símbolo de erro.<br /><br /> Os objetos transmitidos usando o comando são convertidos em um valor de cadeia de caracteres.|`console.error("error message");`|
|`group(title)`|Inicia um agrupamento das mensagens enviadas à janela do console e envia o `title` opcional como um rótulo de grupo. Os grupos podem ser aninhados e aparecer em um modo de exibição de árvore na janela do console.<br /><br /> Os comandos group* podem facilitar a exibição da saída da janela do console em alguns cenários, como quando um modelo de componente está em uso.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|
|`groupCollapsed(title)`|Inicia um agrupamento das mensagens enviadas à janela do console e envia o `title` opcional como um rótulo de grupo. Os grupos enviados usando `groupCollapsed` aparecem em uma exibição recolhida por padrão. Os grupos podem ser aninhados e aparecer em um modo de exibição de árvore na janela do console.|O uso é o mesmo do comando `group`.<br /><br /> Consulte o exemplo do comando `group`.|
|`groupEnd()`|Encerra o grupo atual.<br /><br /> Requisitos:<br /><br /> Visual Studio 2013|Consulte o exemplo do comando `group`.|
|`info(message)`|Envia `message` para a janela do console. A mensagem é prefaciada por um símbolo de informação.|`console.info("info message");`<br /><br /> Para obter mais exemplos, confira [Formatando a saída do console.log](#ConsoleLog) mais adiante neste tópico.|
|`log(message)`|Envia `message` para a janela do console.<br /><br /> Se você transmitir um objeto, este comando o enviará para a janela do console e o exibirá num visualizador de objeto. Você pode usar o visualizador para inspecionar propriedades na janela do console.|`console.log("logging message");`|
|`msIsIndependentlyComposed(element)`|Usado em aplicativos da Web. Sem suporte em aplicativos UWP usando JavaScript.|Não há suporte.|
|`profile(reportName)`|Usado em aplicativos da Web. Sem suporte em aplicativos UWP usando JavaScript.|Não há suporte.|
|`profileEnd()`|Usado em aplicativos da Web. Sem suporte em aplicativos UWP usando JavaScript.|Não há suporte.|
|`select(element)`|Seleciona o HTML especificado `element` no [Explorador do DOM](../debugger/quickstart-debug-html-and-css.md).|console.select(element);|
|`time (name)`|Inicia um temporizador que é identificado pelo parâmetro `name` opcional. Quando usado com `console.timeEnd`, calcula o tempo decorrido entre `time` e `timeEnd` e envia o resultado (medido em ms) ao console usando a cadeia de caracteres `name` como prefixo. Usado para habilitar a instrumentação de código do aplicativo para medir o desempenho.|`console.time("app start");  app.start();  console.timeEnd("app start");`|
|`timeEnd(name)`|Interrompe um temporizador que é identificado pelo parâmetro `name` opcional. Consulte o comando `time` do console.|`console.time("app start"); app.start(); console.timeEnd("app start");`|
|`trace()`|Envia um rastreamento de pilha à janela do console. O rastreamento inclui a pilha de chamadas completa e informações como o nome do arquivo, o número da linha e o número da coluna.|`console.trace();`|
|`warn(message)`|Envia `message` para a janela do console, prefaciada por um símbolo de aviso.<br /><br /> Os objetos transmitidos usando o comando são convertidos em um valor de cadeia de caracteres.|`console.warn("warning message");`|

## <a name="miscellaneous-commands"></a>Comandos variados
Esses comandos também estão disponíveis na janela do Console do JavaScript (não estão disponíveis no código).

|Comando|Descrição|Exemplo|
|-------------|-----------------|-------------|
|`$0`, `$1`, `$2`, `$3`, `$4`|Retorna o elemento especificado para a janela do console. `$0` retorna o elemento selecionado atualmente no Explorador do DOM, `$1` retorna o elemento selecionado anteriormente no Explorador do DOM e assim por diante, até o quarto elemento selecionado anteriormente.|U$3|
|`$(id)`|Retorna um elemento por ID. Este é um comando de atalho para `document.getElementById(id)`, em que `id` é uma cadeia de caracteres que representa a ID do elemento.|`$("contenthost")`|
|`$$(selector)`|Retorna uma matriz de elementos que correspondem ao seletor especificado usando a sintaxe do seletor de CSS. Este é um comando de atalho para `document.querySelectorAll()`.|`$$(".itemlist")`|
|`cd()`<br /><br /> `cd(window)`|Permite que você altere o contexto de avaliação da expressão, da janela de nível superior padrão da página para a janela do quadro especificado. Chamar `cd()` sem parâmetros reverte o contexto para a janela de nível superior.|`cd();`<br /><br /> `cd(myframe);`|
|`select(element)`|Seleciona o elemento especificado no [Explorador do DOM](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|
|`dir(object)`|Retorna um visualizador para o objeto especificado. Você pode usar o visualizador para inspecionar propriedades na janela do console.|`dir(obj);`|

## <a name="checking-whether-a-console-command-exists"></a>Verificando se um comando do console existe
Você pode verificar se um comando específico existe antes de tentar usá-lo. Este exemplo verifica a existência do comando `console.log`. Se `console.log` existir, o código irá chamá-lo.

```javascript
if (console && console.log) {
    console.log("msg");
}

```

## <a name="examining-objects-in-the-javascript-console-window"></a>Examinando objetos na janela Console do JavaScript
Você pode interagir com qualquer objeto que esteja no escopo usando a janela Console do JavaScript. Para inspecionar um objeto fora do escopo na janela do console, use `console.log`, `console.dir` ou outros comandos do seu código. Como alternativa, você pode interagir com o objeto da janela do console enquanto ele estiver no escopo definindo um ponto de interrupção em seu código (ponto de interrupção de inserção do **ponto** de interrupção  >  ).

## <a name="formatting-consolelog-output"></a><a name="ConsoleLog"></a> Formatando a saída do console.log
Se você transmitir diversos argumentos para `console.log`, o console os tratará como uma matriz e concatenará a saída.

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";

console.log(user.first, user.last);
// Output:
// Fred Smith

```

`console.log` também oferece suporte a padrões de substituição "printf" para a formatação da saída. Se você usar padrões de substituição no primeiro argumento, outros argumentos serão usados para substituir os padrões especificados na ordem em que foram usados.

 Há suporte para os seguintes padrões de substituição:

- %s – cadeia de caracteres %i – inteiro %d – inteiro %f – float %o – objeto %b – binário %x – hexadecimal %e –exponente

  Estes são alguns exemplos de como usar padrões de substituição no `console.log`:

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";
user.age = 10.01;
console.log("Hi, %s %s!", user.first, user.last);
console.log("%s is %i years old!", user.first, user.age);
console.log("%s is %f years old!", user.first, user.age);

// Output:
// Hi, Fred Smith!
// Fred is 10 years old!
// Fred is 10.01 years old!
```

## <a name="see-also"></a>Confira também
- [Guia de início rápido: depurar JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017&preserve-view=true)
- [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md?view=vs-2017&preserve-view=true)
