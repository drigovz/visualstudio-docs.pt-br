---
title: Estendendo o JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665761"
---
# <a name="extending-javascript-intellisense"></a>Estendendo JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O recurso de extensibilidade do JavaScript IntelliSense permite que você personalize os resultados do IntelliSense no editor de JavaScript para bibliotecas de terceiros. Isso pode melhorar a experiência de desenvolvedores que usam essas bibliotecas.

 O serviço de linguagem JavaScript fornece recursos do IntelliSense para bibliotecas JavaScript de terceiros que são adicionadas a um projeto. Para a maioria das bibliotecas, a conclusão da instrução é fornecida automaticamente pelo serviço de idioma. A ilustração a seguir mostra um exemplo de conclusão de instrução:

 ![Exemplo de conclusão de instrução](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Se sua biblioteca incluir descrições de variáveis, funções e objetos em marcas de comentário JavaScript padrão (//), você se beneficiará automaticamente, por padrão, dos recursos de extensibilidade do IntelliSense, que fornecem informações descritivas em uma caixa pop-up que aparece à direita dos elementos em uma lista de conclusão ou quando você digita o parêntese de abertura em uma chamada de função. Os comentários na caixa pop-up contêm a descrição do membro. O exemplo a seguir mostra a caixa pop-up para uma lista de conclusão.

 ![Exemplo de uma caixa pop&#45;up de informações rápidas](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Para melhorar ainda mais a experiência do desenvolvedor, você talvez queira fornecer informações de tipo aos desenvolvedores na caixa pop-up. Você pode fornecer informações de tipo usando [comentários de documentação XML](../ide/xml-documentation-comments-javascript.md) do JavaScript em vez de marcas de comentário padrão. Você adiciona comentários de documentação XML usando marcas de comentário de barra tripla (///) e um conjunto definido de elementos XML.

 Como alternativa, você pode fornecer informações de tipo usando a extensibilidade do IntelliSense do JavaScript. Esse recurso permite que você personalize os resultados do IntelliSense criando extensões JavaScript e adicionando-as ao contexto do script. Na extensão, que é um arquivo JavaScript, você assina eventos que são expostos pelo objeto `intellisense` do serviço de idioma. A extensibilidade do JavaScript IntelliSense é a solução preferida para bibliotecas se um padrão de comportamento na biblioteca impedir que o serviço de linguagem JavaScript forneça o nível desejado de suporte IntelliSense e se uma alternativa ao XML declarativo Comentários de documentação também são necessários. Personalizando os resultados do IntelliSense, você pode criar uma experiência IntelliSense de primeira classe, independentemente de quaisquer padrões comportamentais que possam restringir os recursos padrão do serviço de linguagem. Para saber mais, confira [Preenchimento de declaração para identificadores](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Adicionando uma extensão ao contexto do script
 Para que uma extensão do IntelliSense seja executada, ela precisa ser adicionada ao contexto do script atual. A extensão pode ser automaticamente adicionada ao contexto de script pelo mecanismo de descoberta automática, ou você pode adicionar a extensão ao contexto de script manualmente usando grupos de referência ou a diretiva de referência.

 O mecanismo de descoberta automática permite que o serviço de linguagem Localize automaticamente extensões que seguem a Convenção de nomenclatura de arquivo *LibraryName*. IntelliSense. js e que estão localizadas no mesmo diretório que a biblioteca à qual a extensão às. Por exemplo, uma extensão válida para a biblioteca jQuery é jQuery. IntelliSense. js. Para extensões jQuery mais restritivas, você pode usar nomes de arquivo como jQuery-1.7.1. IntelliSense. js (uma extensão específica de versão) ou jQuery. UI. IntelliSense. js (uma extensão para uma biblioteca do jQuery com escopo). A versão mais restritiva da extensão será usada se mais de uma extensão for encontrada para uma determinada biblioteca.

 Se você quiser usar a extensão para todos os seus arquivos de projeto JavaScript, você pode optar por adicionar a extensão a um grupo de referência. Há vários tipos de grupos de referência, ou seja, aqueles que incluem referências implícitas e aqueles que incluem referências de trabalhador dedicadas. Para adicionar uma extensão, normalmente você precisa adicionar o arquivo como um grupo de referência implícito, **implícito (Windows)** , **implícito (Web)** . As referências implícitas estão no escopo para cada arquivo. js aberto no editor de código. Ao usar esse método, você precisa adicionar a extensão e o arquivo que a extensão está complementando.

 Use a página **IntelliSense** da caixa de diálogo **Opções** para adicionar uma extensão como um grupo de referência. Você pode acessar a página do **IntelliSense** escolhendo **ferramentas**, **Opções** na barra de menus e, em seguida, escolhendo o **Editor de texto**, **JavaScript**, **IntelliSense**, **referências**. Para obter mais informações sobre grupos de referência, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md) and [Options, text editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Se você quiser usar a extensão para um conjunto específico de arquivos, use uma diretiva de referência. Ao usar esse método, você precisa referenciar a extensão e o arquivo que a extensão está complementando. Para obter informações sobre como usar a diretiva de referência, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>Manipulando eventos do IntelliSense
 O recurso de extensibilidade permite que você personalize os resultados do IntelliSense assinando eventos como o `statementcompletion` evento do objeto de `intellisense` de serviço de linguagem. O exemplo a seguir mostra uma extensão simples usada pelo serviço de linguagem para ocultar membros que começam com um sublinhado da conclusão da instrução. Esse código está contido em underscorefilter. js e está na pasta \\ \\*caminho de instalação do Visual Studio*\JavaScript\References.

```javascript
intellisense.addEventListener('statementcompletion', function (event) {
    if (event.targetName === "this") return;

    var filterRegex;

    if (event.target === undefined || event.target === window)
        filterRegex = /^_.*\d{2,}/;
    else
        filterRegex = /^_.*/;

    event.items = event.items.filter(function (item) {
        return !filterRegex.test(item.name);
    });
});
```

 No código anterior, a extensão verifica a [Propriedade TargetName](#TargetName) e as propriedades de [propriedade de destino](#Target) do objeto de evento `statementcompletion` para excluir objetos, como `this` e `window`, e para garantir que uma lista de conclusão de instrução válida possa ser Identifica. Se uma lista de conclusão puder ser identificada, a extensão atualizará a coleção de [Propriedades de itens](#Items) de conclusão de instrução filtrando os membros que começam com um sublinhado.

 Para obter exemplos adicionais, consulte a pasta \\ \\*caminho de instalação do Visual Studio*\JavaScript\References. O arquivo showPlainComments. js nessa pasta fornece exemplos de como usar outros eventos para fornecer suporte padrão ao IntelliSense para marcas de comentário JavaScript padrão (//). Como o underscorefilter. js, o showPlainComments. js já está disponível como uma extensão de trabalho, e você pode ver as informações resultantes do IntelliSense ao usar marcas de comentário em seu código para variáveis, funções e objetos. Para obter exemplos adicionais, consulte [exemplos de código](#CodeExamples).

> [!WARNING]
> Se você modificar os arquivos de extensão incluídos no Visual Studio, poderá desabilitar o IntelliSense do JavaScript ou o recurso suportado pela extensão.

 Em seu código de extensão, você pode criar manipuladores para os seguintes tipos de evento usando `addEventListener`:

- `statementcompletion`, que adiciona um manipulador para um evento de conclusão de instrução. A conclusão da instrução fornece uma lista de membros para um tipo específico que aparece depois que você digita um caractere especial, como um ponto (.), ou uma lista de identificadores que aparece enquanto você digita ou pressiona CTRL + J. O manipulador recebe um objeto de evento do tipo `CompletionEvent`, que dá suporte aos seguintes membros: [propriedade de itens](#Items), [propriedade de destino](#Target), [Propriedade TargetName](#TargetName)e [propriedade de escopo](#Scope).

- `signaturehelp`, que adiciona um manipulador para informações de parâmetro do IntelliSense. Informações de parâmetro fornecem informações sobre o número, os nomes e os tipos de parâmetros exigidos por uma função. O manipulador recebe um objeto de evento do tipo `SignatureHelpEvent`, que dá suporte aos seguintes membros: [propriedade de destino](#Target), [propriedade ParentObject](#ParentObject), [Propriedade functionComments](#FunctionComments), [Propriedade functionHelp](#FunctionHelp).

- `statementcompletionhint`, que adiciona um manipulador para informações rápidas do IntelliSense. A caixa pop-up informações rápidas mostra a declaração completa para identificadores em seu código. O manipulador recebe um objeto de evento do tipo `CompletionHintEvent`, que dá suporte aos seguintes membros: [Propriedade completionItem](#CompletionItem)e [Propriedade symbolHelp](#SymbolHelp).

  Para obter exemplos que mostram recursos do IntelliSense, como conclusão de instrução, informações de parâmetro e informações rápidas, consulte [usando o IntelliSense](../ide/using-intellisense.md).

> [!NOTE]
> No JavaScript, informações rápidas referem-se à caixa pop-up que aparece à direita de uma lista de conclusão. Você não pode invocar manualmente informações rápidas.

## <a name="intellisenseObject"></a> Objeto intellisense
 A tabela a seguir mostra as funções que estão disponíveis para o objeto `intellisense`. O objeto `intellisense` está disponível somente no momento do design.

|Função|{1&gt;Descrição&lt;1}|
|--------------|-----------------|
|`addEventListener(type, handler);`|Adiciona um manipulador de eventos para um evento do IntelliSense.<br /><br /> `type` é um valor de cadeia de caracteres. Os valores válidos incluem `statementcompletion`, `signaturehelp` e `statementcompletionhint`.<br /><br /> `handler` é uma função de manipulador de eventos que recebe um objeto de evento de um dos seguintes tipos:<br /><br /> -    `CompletionEvent`, usado para o evento `statementcompletion`.<br />-    `SignatureHelpEvent`, usado para o evento `signaturehelp`.<br />-    `CompletionHintEvent`, usado para o evento `statementcompletionhint`.<br /><br /> Para obter exemplos que usam essa função, consulte [exemplos de código](#CodeExamples).|
|`annotate(obj, doc);`|Especifica a documentação de um objeto copiando comentários de documentação de um objeto para outro objeto.<br /><br /> `obj` especifica o objeto para o qual copiar a documentação.<br /><br /> `doc` especifica o objeto do qual copiar a documentação.<br /><br /> Para obter um exemplo que mostra como usar essa função, consulte [Adicionando anotações do IntelliSense](#Annotations).|
|`getFunctionComments(func);`|Retorna os comentários para uma função especificada.<br /><br /> `func` especifica a função para a qual os comentários são retornados.<br /><br /> Você pode definir o parâmetro `func` usando `completionItem.value`.<br /><br /> O objeto `functionComments` retornado inclui os seguintes membros: `above`, `inside` e `paramComment`. Para obter mais informações, consulte a propriedade da [Propriedade functionComments](#FunctionComments) .<br /><br /> `getFunctionComments` pode ser chamado somente de dentro de um dos manipuladores de eventos registrados pelo `addEventListener`.<br /><br /> Para obter um exemplo que mostra como usar essa função, consulte \\ \\*caminho de instalação do Visual Studio*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Envia mensagens de diagnóstico para a janela de saída.<br /><br /> `msg` é uma cadeia de caracteres que contém a mensagem.<br /><br /> Para obter um exemplo que mostra como usar essa função, consulte [enviando mensagens para o janela de saída](#Logging).|
|`nullWithCompletionsOf(value);`|Retorna um valor nulo especial para o qual a lista de conclusão é determinada pelo objeto passado no parâmetro `value`.<br /><br /> `value` determina a lista de conclusão para o valor retornado. `value` pode ser qualquer tipo.<br /><br /> O valor de retorno nulo é tratado como nulo em tempo de design, mas a lista de conclusão do valor de retorno é igual à lista de conclusão do parâmetro `value`.<br /><br /> Um uso para essa função é fornecer IntelliSense para um valor de retorno quando o tipo de retorno é previsível em tempo de execução, mas o valor de retorno é `null` no momento do design.|
|`redirectDefinition(func, definition);`|Instrui o IntelliSense a usar a função de definição fornecida em vez da função Func original quando a ajuda de parâmetro ou **ir para definição** for solicitada.<br /><br /> `func` especifica a função de destino.<br /><br /> `definition` especifica a função a ser usada em vez da função de destino para informações de parâmetro e **vai para a definição**.|
|`setCallContext(func, thisArg);`|Define o contexto de chamada, ou escopo, para a função especificada.<br /><br /> `func` especifica a função para a qual definir o escopo.<br /><br /> `thisArg` é um literal de objeto ao qual a palavra-chave `this` pode se referir, que especifica o novo escopo para o membro. Você pode incluir argumentos para passar esse parâmetro, por exemplo, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` fornece comportamento semelhante ao `Function.prototype.bind`, exceto pelo fato de que ele é usado apenas para suporte ao IntelliSense em tempo de design. Você pode usar `setCallContext` para definir o escopo da função se precisar simular uma chamada para código que não seja acessível, de modo que, ao chamar a função, a chamada de função incluirá o escopo e os argumentos corretos.|
|`undefinedWithCompletionsOf(value);`|Retorna um valor especial indefinido para o qual a lista de conclusão é determinada pelo objeto passado no parâmetro `value`.<br /><br /> `value` determina a lista de conclusão para o valor retornado. `value` pode ser qualquer tipo.<br /><br /> O valor de retorno indefinido é tratado como indefinido em tempo de design, mas a lista de conclusão do valor de retorno é igual à lista de conclusão do parâmetro `value`.<br /><br /> Um uso para essa função é fornecer IntelliSense para um valor de retorno quando o tipo de retorno é previsível em tempo de execução, mas o valor de retorno é indefinido no momento do design.|
|`version()`|Retorna a versão do Visual Studio.|

## <a name="event-members"></a>Membros do evento
 As seções a seguir descrevem os membros que são expostos no objeto de evento para os seguintes eventos: `statementcompletion`, `signaturehelp` e `statementcompletionhint`.

### <a name="CompletionItem"></a>Propriedade completionItem
 Retorna o identificador, conhecido como o item de conclusão, para o qual uma caixa pop-up de informações rápidas é solicitada. Essa propriedade está disponível para o objeto de evento `statementcompletionhint` e para a propriedade de [propriedade Items](#Items) do objeto de evento `statementcompletion`.

 Valor de retorno: objeto `completionItem`

 A seguir estão os membros do objeto `completionItem`:

- [https://aka.ms/AzureNVblog](`name`). Leitura/gravação quando usada na coleção de `items`; caso contrário, somente leitura. Retorna uma cadeia de caracteres que identifica o item de conclusão.

- [https://aka.ms/AzureNVblog](`kind`). Leitura/gravação quando usada na coleção de `items`; caso contrário, somente leitura. Retorna uma cadeia de caracteres que representa o tipo de item de conclusão. Os valores possíveis são método, campo, propriedade, parâmetro, variável e reservado.

- [https://aka.ms/AzureNVblog](`glyph`). Leitura/gravação quando usada na coleção de `items`; caso contrário, somente leitura. Retorna uma cadeia de caracteres que representa um ícone que é exibido na lista de conclusão. Os valores possíveis para `glyph` usam o seguinte formato: vs:*glyphstype*, em que *glifotype* corresponde aos membros independentes de linguagem na enumeração <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>. Por exemplo, `vs:GlyphGroupMethod` é um valor possível para `glyph`. Quando `glyph` não é definido, a propriedade `kind` determina o ícone padrão.

- [https://aka.ms/AzureNVblog](`parentObject`). Somente leitura. Retorna o objeto pai.

- [https://aka.ms/AzureNVblog](`value`). Somente leitura. Retorna um objeto que representa o valor do item de conclusão.

- [https://aka.ms/AzureNVblog](`comments`). Somente leitura. Retorna uma cadeia de caracteres que contém os comentários que estão acima do campo ou da variável.

- [https://aka.ms/AzureNVblog](`scope`). Somente leitura. Retorna o escopo do item de conclusão. Os valores possíveis são global, local, parâmetro e membro.

### <a name="Items"></a>Propriedade Items
 Obtém ou define a matriz de itens de conclusão de instrução. Cada elemento na matriz é um objeto de [Propriedade completionItem](#CompletionItem) . A propriedade `items` está disponível para o objeto de evento `statementcompletion`.

 Valor de retorno: matriz

### <a name="FunctionComments"></a>Propriedade functionComments
 Retorna os comentários para a função. Essa propriedade está disponível para o objeto de evento `signaturehelp`.

 Valor de retorno: objeto `comments`

 A seguir estão os membros do objeto `comments`:

- [https://aka.ms/AzureNVblog](`above`). Retorna os comentários acima da função.

- [https://aka.ms/AzureNVblog](`inside`). Retorna os comentários dentro da função, normalmente no formato VSDoc.

- [https://aka.ms/AzureNVblog](`paramComments`). Retorna uma matriz que representa os comentários para cada parâmetro na função. Os membros da matriz incluem:

  - [https://aka.ms/AzureNVblog](`name`). Retorna uma cadeia de caracteres que representa o nome do parâmetro.

  - [https://aka.ms/AzureNVblog](`comment`). Retorna uma cadeia de caracteres que contém o comentário do parâmetro.

### <a name="FunctionHelp"></a>Propriedade functionHelp
 Retorna a ajuda para a função. Essa propriedade está disponível para o objeto de evento `signaturehelp`.

 Valor de retorno: objeto `functionHelp`

 A seguir estão os membros do objeto `functionHelp`:

- [https://aka.ms/AzureNVblog](`functionName`). Leitura/gravação. Retorna uma cadeia de caracteres que contém o nome da função.

- [https://aka.ms/AzureNVblog](`signatures`). Leitura/gravação. Obtém ou define a matriz de assinaturas de função. Cada elemento na matriz é um objeto `signature`. Algumas propriedades `signature`, como `locid`, correspondem aos atributos comuns de [comentários de documentação XML](../ide/xml-documentation-comments-javascript.md) .

  Os membros do objeto `signature` incluem:

  - [https://aka.ms/AzureNVblog](`description`). Leitura/gravação. Retorna uma cadeia de caracteres que descreve a função.

  - [https://aka.ms/AzureNVblog](`locid`). Leitura/gravação. Retorna um identificador de cadeia de caracteres que contém informações de localização sobre a função.

  - [https://aka.ms/AzureNVblog](`helpKeyword`). Leitura/gravação. Retorna uma cadeia de caracteres que contém a palavra-chave help.

  - [https://aka.ms/AzureNVblog](`externalFile`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o arquivo que contém a ID do membro.

  - [https://aka.ms/AzureNVblog](`externalid`). Leitura/gravação. Retorna uma cadeia de caracteres que representa a ID de membro da função.

  - [https://aka.ms/AzureNVblog](`params`). Leitura/gravação. Obtém ou define a matriz de parâmetros para a função. Cada elemento na matriz Parameters é um objeto `parameter` que tem propriedades que correspondem aos seguintes atributos do elemento [\<param >](../ide/param-javascript.md) :

    - [https://aka.ms/AzureNVblog](`name`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o nome do parâmetro.

    - [https://aka.ms/AzureNVblog](`type`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o tipo de parâmetro.

    - [https://aka.ms/AzureNVblog](`elementType`). Leitura/gravação. Se o tipo for `Array`, retornará uma cadeia de caracteres que representa o tipo dos elementos na matriz.

    - [https://aka.ms/AzureNVblog](`description`). Leitura/gravação. Retorna uma cadeia de caracteres que descreve o parâmetro.

    - [https://aka.ms/AzureNVblog](`locid`). Leitura/gravação. Retorna um identificador de cadeia de caracteres que contém informações de localização sobre a função.

    - [https://aka.ms/AzureNVblog](`optional`). Leitura/gravação. Retorna uma cadeia de caracteres que indica se o parâmetro é opcional. `true` indica que o parâmetro é opcional;  `false` indica que não é.

  - [https://aka.ms/AzureNVblog](`returnValue`). Leitura/gravação. Obtém ou define um objeto de valor de retorno com propriedades que correspondem aos seguintes atributos do elemento [\<returns >](../ide/returns-javascript.md) :

    - [https://aka.ms/AzureNVblog](`type`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o tipo de retorno.

    - [https://aka.ms/AzureNVblog](`elementType`). Leitura/gravação. Se o tipo for `Array`, retornará uma cadeia de caracteres que representa o tipo dos elementos na matriz.

    - [https://aka.ms/AzureNVblog](`description`). Leitura/gravação. Retorna uma cadeia de caracteres que descreve o valor de retorno.

    - [https://aka.ms/AzureNVblog](`locid`). Leitura/gravação. Retorna um identificador de cadeia de caracteres que contém informações de localização sobre a função.

    - [https://aka.ms/AzureNVblog](`helpKeyword`). Leitura/gravação. Retorna uma cadeia de caracteres que contém a palavra-chave help.

    - [https://aka.ms/AzureNVblog](`externalFile`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o arquivo que contém a ID do membro.

    - [https://aka.ms/AzureNVblog](`externalid`). Leitura/gravação. Retorna uma cadeia de caracteres que representa a ID de membro da função.

### <a name="ParentObject"></a>Propriedade ParentObject
 Retorna o objeto pai de uma função de membro. Por exemplo, para `document.getElementByID`, `parentObject` retorna o objeto `document`. Essa propriedade está disponível para o objeto de evento `signaturehelp`.

 Valor de retorno: objeto

### <a name="Target"></a> Propriedade target
 Retorna um objeto que representa o item à esquerda do caractere de gatilho, que é um ponto final (.). Para funções, `target` retorna a função para a qual as informações de parâmetro são solicitadas. Essa propriedade está disponível para os objetos de evento `statementcompletion` e `signaturehelp`.

 Valor de retorno: objeto

### <a name="TargetName"></a>Propriedade targetName
 Retorna uma cadeia de caracteres que representa o destino. Por exemplo, para "this.", `targetName` retorna "This". Para "A. B" (quando o cursor é após "B"), `targetName` retorna "B". Essa propriedade está disponível para o objeto de evento `statementcompletion`.

 Valor de retorno: cadeia de caracteres

### <a name="SymbolHelp"></a>Propriedade symbolHelp
 Retorna o item de conclusão para o qual uma caixa pop-up de informações rápidas é solicitada. Essa propriedade está disponível para o objeto de evento `statementcompletionhint`.

 Valor de retorno: `symbolHelp` objeto.

 Algumas propriedades do objeto `symbolHelp`, como `locid`, correspondem aos atributos comuns de [comentários de documentação XML](../ide/xml-documentation-comments-javascript.md) .

 A seguir estão os membros do objeto `symbolHelp`:

- [https://aka.ms/AzureNVblog](`name`). Leitura/gravação. Retorna uma cadeia de caracteres que contém o nome do identificador.

- [https://aka.ms/AzureNVblog](`symbolType`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o tipo de símbolo. Os valores possíveis incluem desconhecido, booliano, número, Cadeia de caracteres, objeto, função, matriz, data e Regex.

- [https://aka.ms/AzureNVblog](`symbolDisplayType`). Leitura/gravação. Retorna uma cadeia de caracteres que contém o nome do tipo a ser exibido. Se `symbolDisplayType` não estiver definido, `symbolType` será usado.

- [https://aka.ms/AzureNVblog](`elementType`). Leitura/gravação. Se o `symbolType` for `Array`, retornará uma cadeia de caracteres que representa o tipo dos elementos na matriz.

- [https://aka.ms/AzureNVblog](`scope`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o escopo do símbolo. Os valores possíveis incluem global, local, parâmetro e membro.

- [https://aka.ms/AzureNVblog](`description`). Leitura/gravação. Retorna uma cadeia de caracteres que contém uma descrição do símbolo.

- [https://aka.ms/AzureNVblog](`locid`). Leitura/gravação. Retorna um identificador de cadeia de caracteres que contém informações de localização sobre o símbolo.

- [https://aka.ms/AzureNVblog](`helpKeyword`). Leitura/gravação. Retorna uma cadeia de caracteres que contém a palavra-chave help.

- [https://aka.ms/AzureNVblog](`externalFile`). Leitura/gravação. Retorna uma cadeia de caracteres que representa o arquivo que contém a ID do membro.

- [https://aka.ms/AzureNVblog](`externalid`). Leitura/gravação. Retorna uma cadeia de caracteres que representa a ID de membro do símbolo.

- [https://aka.ms/AzureNVblog](`functionHelp`). Leitura/gravação. Retorna uma [Propriedade functionHelp](#FunctionHelp), que pode conter informações quando o `symbolType` é função.

### <a name="Scope"></a>Propriedade de escopo
 Retorna o escopo de conclusão do evento. Os valores possíveis para o escopo de conclusão são global e Members. Essa propriedade está disponível para o objeto de evento `statementcompletion`.

 Valor de retorno: cadeia de caracteres

## <a name="debugging-intellisense-extensions"></a>Depuração de extensões do IntelliSense
 Você não pode depurar extensões, mas pode usar a função de [objeto IntelliSense](#intellisenseObject) para enviar informações para a janela de saída do Visual Studio. Para obter um exemplo que mostra como usar essa função, consulte [enviando mensagens para o janela de saída](#Logging) mais adiante neste tópico. Para que `logMessage` funcionem, pelo menos um manipulador de eventos deve ser registrado em uma extensão.

## <a name="CodeExamples"></a> Exemplos de código
 Esta seção inclui exemplos de código que mostram como usar as APIs de extensibilidade do IntelliSense. Também há outras maneiras de usar essas APIs. Para obter exemplos adicionais, consulte os seguintes arquivos na pasta \\ \\*caminho de instalação do Visual Studio*\JavaScript\References Esses são exemplos de trabalho usados pelo serviço de linguagem JavaScript.

- underscoreFilter.js. Esse código oculta os membros privados do IntelliSense. Ele inclui manipuladores de eventos para o evento `statementcompletion`.

- showPlainComments.js. Esse código fornece suporte IntelliSense para comentários padrão. Ele inclui manipuladores de eventos para os eventos `signaturehelp` e `statementcompletionhint`.

### <a name="Annotations"></a>Adicionando anotações do IntelliSense
 O procedimento a seguir mostra como fornecer suporte de documentação do IntelliSense para uma biblioteca de terceiros sem modificar a biblioteca diretamente. Para fazer isso, você pode usar `intellisense.annotate` em uma extensão.

 Para que este exemplo funcione, você precisa dos seguintes arquivos JavaScript em seu projeto:

- demoLib. js, que é um arquivo de projeto que representa uma biblioteca de terceiros.

- demoLib. IntelliSense. js, que é a extensão do IntelliSense. Esse arquivo não precisa ser incluído no projeto, mas ele precisa estar na mesma pasta que exampleLib. js.

- appCode. js, que é um arquivo de projeto que representa o código do aplicativo.

##### <a name="to-add-an-intellisense-annotation"></a>Para adicionar uma anotação do IntelliSense

1. Adicione o código a seguir a demoLib. js.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. Adicione o código a seguir a demoLib. IntelliSense. js.

    ```javascript
    intellisense.annotate(someFunc, function (a) {
        /// <signature>
        /// <summary>Description of someFunc</summary>
        /// <param name="a">Param a</param>
        /// </signature>
    });

    intellisense.annotate(window, {
        // This is a comment on a global variable named rectangle.
        rectangle: undefined
    });
    ```

3. Adicione a seguinte diretiva de referência como a primeira linha em appCode. js. O caminho usado aqui indica que os arquivos JavaScript estão na mesma pasta.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. Em appCode. js, digite o código a seguir. Você verá os comentários de documentação XML na extensão exibida como informações de parâmetro do IntelliSense.

     ![Exemplo mostrando o uso do IntelliSense. anotar](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. Em appCode. js, digite o código a seguir. Ao digitar, você verá os comentários padrão na extensão exibida como informações rápidas do IntelliSense.

     ![Exemplo mostrando o uso do IntelliSense. anotar](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="Logging"></a>Enviando mensagens para o Janela de Saída
 O procedimento a seguir mostra como enviar mensagens para a janela de saída. Você pode enviar mensagens para ajudar a depurar extensões do IntelliSense.

 Para que este exemplo funcione, você precisa dos seguintes arquivos JavaScript em seu projeto:

- exampleLib. js, que é um arquivo de projeto que representa uma biblioteca de terceiros.

- exampleLib. IntelliSense. js, que é a extensão do IntelliSense. Esse arquivo não precisa ser incluído no projeto, mas ele precisa estar na mesma pasta que exampleLib. js.

- appCode. js, que é um arquivo de projeto que representa o código do aplicativo.

##### <a name="to-send-a-message-to-the-output-window"></a>Para enviar uma mensagem para a janela de saída

1. Adicione o código a seguir a exampleLib. js.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. Adicione o código a seguir a exampleLib. IntelliSense. js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        // Prints out statement completion info: Either (1) the member
        // list, if the trigger character was typed, or (2) the
        // statement completion identifiers.
        // e.target represents the object left of the trigger character.
        intellisense.logMessage(
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');

        // Prints out all statement completion items.
        e.items.forEach(function (item) {
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);
        });
    });
    ```

3. Adicione a seguinte diretiva de referência como a primeira linha em appCode. js. O caminho usado aqui indica que os arquivos JavaScript estão na mesma pasta.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. Na janela saída, escolha **JavaScript Language Service** na lista **Mostrar saída de** . (Para exibir a janela saída, selecione **saída** no menu Exibir.)

5. Em appCode. js, digite o código a seguir. Enquanto você digita, a janela saída mostra as mensagens do serviço de idioma. A primeira mensagem na janela de saída indica que a conclusão da instrução para o escopo atual foi solicitada.

    ```javascript
    some
    ```

     A seguir está uma exibição parcial da saída que você deve ver.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Escolha o botão **limpar tudo** na janela saída.

7. Digite o código a seguir. A primeira mensagem na janela de saída indica que uma lista de membros foi solicitada.

    ```javascript
    someVar.
    ```

     A seguir está uma exibição parcial da saída que você deve ver:

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="Icons"></a>Alterando os ícones do IntelliSense
 O procedimento a seguir mostra como alterar os ícones exibidos pelo IntelliSense por padrão. Isso pode ser útil quando você fornece informações do IntelliSense sobre conceitos específicos da biblioteca, como namespaces, classes, interfaces e enumerações.

 Para obter os valores de ícone disponíveis, consulte <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.

 Para que este exemplo funcione, você precisa dos seguintes arquivos JavaScript em seu projeto:

- exampleLib. js, que é um arquivo de projeto que represens uma biblioteca de terceiros.

- exampleLib. IntelliSense. js, que é a extensão do IntelliSense. Esse arquivo não precisa ser incluído no projeto, mas ele precisa estar na mesma pasta que exampleLib. js.

- appCode. js, que é um arquivo de projeto que representa o código do aplicativo.

##### <a name="to-change-the-icons"></a>Para alterar os ícones

1. Adicione o código a seguir a exampleLib. js.

    ```javascript
    function Namespace(name) {
        this._isNamespace = true;
        window[name] = this;
    };

    function Enum(values) {
        var e = Object.create(values);
        e._isEnum = true;
        return e;
    };

    var SomeNamespace = new Namespace('SomeNamespace');
    // A constructor function is considered a class.
    SomeNamespace.SomeClass1 = function () { }
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });
    ```

2. Adicione o código a seguir a exampleLib. IntelliSense. js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        e.items.forEach(function (item) {
            // Detect a namespace by using the _isNamespace flag.
            if (item.value && item.value._isNamespace) {
                item.glyph = 'vs:GlyphGroupNamespace';
                }

            if (item.parentObject && item.parentObject._isNamespace) {
                // The item is a member of a namespace.

                // All constructor functions that are part of a namespace
                // are considered classes.
                // A constructor function starts with
                // an uppercase letter by convention.
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()
                    == item.name[0])) {
                    item.glyph = 'vs:GlyphGroupClass';
                }

                // Detect an enumeration by using the _isEnum flag.
                if (item.value && item.value._isEnum) {
                    item.glyph = 'vs:GlyphGroupEnum';
                }
            }
        });
    });

    intellisense.addEventListener('statementcompletionhint', function (e) {
        if (e.completionItem.value) {
            if (e.completionItem.value._isNamespace) {
                e.symbolHelp.symbolDisplayType = 'Namespace';
            }
            if (e.completionItem.value._isEnum) {
                e.symbolHelp.symbolDisplayType = 'Enum';
            }
        }
    });
    ```

3. Adicione a seguinte diretiva de referência como a primeira linha em appCode. js. O caminho usado aqui indica que os arquivos JavaScript estão na mesma pasta.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. Em appCode. js, digite o código a seguir. Ao digitar, você verá que o ícone do namespace foi alterado para "{}", como é usado no C#.

     ![Exemplo mostrando o uso da Propriedade Glyphs](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. Em appCode. js, digite o código a seguir. Ao digitar, você verá um novo ícone de enumeração para o membro Enum1 e um novo ícone de classe para o membro SomeClass1.

     ![Exemplo mostrando o uso da Propriedade Glyphs](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="Overriding"></a>Evitando efeitos de tempo de execução nos resultados do IntelliSense
 O serviço de linguagem JavaScript executa o código para fornecer informações do IntelliSense dinamicamente. Como resultado, o comportamento de tempo de execução pode interferir ocasionalmente nos resultados desejados. O procedimento a seguir mostra como substituir os resultados do IntelliSense quando o comportamento de tempo de execução resulta em um IntelliSense incorreto.

 Para que este exemplo funcione, você precisa dos seguintes arquivos JavaScript em seu projeto:

- exampleLib. js, que é um arquivo de projeto que representa uma biblioteca de terceiros.

- exampleLib. IntelliSense. js, que é a extensão do IntelliSense. Esse arquivo não precisa ser incluído no projeto, mas ele precisa estar na mesma pasta que exampleLib. js.

- appCode. js, que é um arquivo de projeto que representa o código do aplicativo.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Para evitar efeitos de tempo de execução nos resultados do IntelliSense

1. Adicione o código a seguir a exampleLib. js.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     No código anterior, a função wrapped ignora as chamadas iniciais, com base no valor de `count` e não retorna resultados.

2. Adicione a seguinte diretiva de referência como a primeira linha em appCode. js. O caminho usado aqui indica que os arquivos JavaScript estão na mesma pasta.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. Em appCode. js, digite o código a seguir. A lista identificador é exibida em vez do IntelliSense porque a função encapsulada nunca é chamada, o que significa que a função `throttled` não retorna nenhum resultado.

     ![Exemplo de substituição de resultados do IntelliSense](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. Adicione o código a seguir a exampleLib. IntelliSense. js. Isso alterará o comportamento de tempo de design para que o IntelliSense seja mostrado para a função encapsulada, conforme esperado.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. Em appCode. js, teste os resultados digitando o mesmo código que você digitou anteriormente. Desta vez, o IntelliSense fornece as informações desejadas.

     ![Exemplo de substituição de resultados do IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>Consulte também
 [Conclusão da instrução para identificadores](../ide/statement-completion-for-identifiers.md) do [JavaScript IntelliSense](../ide/javascript-intellisense.md)
