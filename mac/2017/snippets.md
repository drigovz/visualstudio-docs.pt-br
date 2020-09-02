---
title: Snippets de código
description: Como usar snippets de código para programar de forma eficiente no Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 96344b72dd27095f8b9060078112fb767b1338fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984814"
---
# <a name="code-snippets"></a>Snippets de código

Snippets de código, geralmente chamados de _modelos de código_, são úteis para obter uma programação eficiente, já que permitem a inserção e a edição de blocos de código previamente escritos. O uso de snippets de código pode ser conveniente para adicionar rapidamente padrões comuns ou até mesmo para conhecer novos padrões quando, como desenvolvedor, você não tiver certeza sobre a sintaxe. Há modelos fornecidos para C#, F#, HTML, XML, Python e Razor.

Esta seção explica como criar, inserir e usar snippets no código.

## <a name="inserting-a-snippet"></a>Inserindo um snippet

Há algumas maneiras de adicionar snippets de código, algumas das quais são descritas abaixo:

- **Guia Expansão** &ndash; Comece digitando o nome do modelo, selecione-o na lista e pressione **Tab**, **Tab** para adicioná-lo:

  ![Guia Expansão no código](media/source-editor-image13.png)

- **Caixa de ferramentas** &ndash; Use o painel da caixa de ferramentas para exibir uma lista de todos os snippets de código. Arraste qualquer modelo da caixa de ferramentas para a posição correta no código-fonte:

  [![Trechos de código na caixa de ferramentas](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Comando Inserir Modelos** &ndash; Atualmente, não há nenhuma associação de teclas definida para a inserção de modelos. Para criar uma, navegue até **Visual Studio > Preferências > Associações de teclas** e pesquise `template`. Isso permite adicionar a associação de teclas desejada no campo Editar associação e clicar em **Aplicar**:

  ![Comando Inserir Modelo](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Criando um novo modelo

Embora haja muitos modelos existentes em uma variedade de linguagens que você pode usar e editar, novos modelos também podem ser adicionados navegando para **Visual Studio &gt; Preferências &gt; Editor de texto &gt; Snippets de código**:

![Inserir novo modelo](media/source-editor-image12.png)

Pressione os botões **Adicionar** ou **Editar** para criar ou editar snippets.

## <a name="keywords-in-code-snippets"></a>Palavras-chave em snippets de código

Depois da inserção de um snippet de código no editor, as palavras-chave definidas são realçadas e podem ser editadas usando tabulações entre elas. Palavras-chave se comportam como uma "variável" no snippet de código. Para defini-las, coloca-se um sinal de cifrão `$` antes e após o nome da palavra-chave. 

A janela **Editar modelo** é exibida abaixo, editando o snippet `prop` interno. O trecho de código contém duas palavras-chave &ndash; `$type$` e `$name$` &ndash; que podem ter propriedades adicionais definidas (como um valor padrão e uma dica de ferramenta) no lado direito da janela:

![Janela Editar modelo](media/source-editor-image12z.png)

Os campos a seguir servem para definir um snippet:

- **Atalho** &ndash; O texto que o usuário digita para inserir o snippet.
- **Agrupar** &ndash; Os snippets são agrupados no menu de conteúdo do snippet usando este valor.
- **Descrição** &ndash; Explicação sobre a finalidade do snippet.
- **MIME** &ndash; Controla em quais tipos de arquivo o snippet está disponível.
- **Modelo Expansível** &ndash; Marque esta opção para que o snippet possa ser inserido no cursor, ao digitar o atalho.
- **Modelo surround with** &ndash; Marque esta opção para exibir este atalho no menu de conteúdo **Surround with...** do editor.
- **Modelo de texto** &ndash; O snippet real que será inserido no editor. É possível definir espaços reservados para palavras-chave adicionando sinais de cifrão ao redor de um token; por exemplo, `$type$`.
- **Painel de propriedades de palavra-chave** &ndash; No lado direito da janela, use a lista suspensa na parte superior para escolher uma palavra-chave, por exemplo, `type`, e edite propriedades, como um valor padrão ou uma dica de ferramenta.

## <a name="using-keywords-in-the-editor"></a>Como usar palavras-chave no editor

Para usar um snippet com palavras-chave, como a definida acima, digite o atalho e pressione a tecla **Tab** duas vezes para que o conteúdo do snippet seja inserido no cursor:

![Snippet inserido mostrando palavras-chave](media/source-editor-image12a.png)

Pressione a tecla **Tab** para navegar entre `object` e `MyProperty` a fim de personalizar o snippet para a classe.

É possível repetir uma palavra-chave no snippet, como o exemplo `for`. Observe que a palavra-chave `$i$` é exibida três vezes:

![Modelo de snippet com palavras-chave repetidas](media/source-editor-image12b.png)

Quando usado no editor, a tecla **Tab** alternará entre a primeira instância de `i` e `max`. Se você sobrescrever `i` com um nome variável diferente, as três instâncias serão atualizadas:

![Snippet inserido mostrando várias palavras-chave](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Palavras-chave reservadas

Há duas palavras-chave reservadas que você pode usar em um snippet de código:

- `$selected$` &ndash; Se o snippet tiver a opção **Modelo surround with** marcada, esta palavra-chave será substituída pelo texto que foi realçado no editor quando o snippet foi escolhido.
- `$end$`&ndash;Quando o usuário terminar de editar as palavras-chave em um trecho de código, o cursor será colocado no local da `$end$` palavra-chave.

O snippet `for` da seção anterior é um exemplo de palavras-chave reservadas.

Para saber mais, confira o tópico [Referência de snippets de código do Visual Studio](/visualstudio/ide/code-snippets-schema-reference#keywords).

## <a name="see-also"></a>Confira também

- [Snippets de código (Visual Studio no Windows)](/visualstudio/ide/code-snippets)