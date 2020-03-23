---
title: Editar o código R
description: O Visual Studio fornece uma experiência de edição personalizada para R, mantendo todos os recursos e a capacidade de usar extensões.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302710"
---
# <a name="edit-r-code-in-visual-studio"></a>Editar o código R no Visual Studio

As RTVS (Ferramentas do R para Visual Studio) personalizam a experiência de edição do Visual Studio especificamente para R, mantendo todos os recursos e a capacidade de usar extensões. (Por exemplo, se preferir associações de teclas VIM, será possível instalar a [extensão VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) gratuita do Visual Studio Marketplace.)

Além dos recursos neste artigo, veja também [IntelliSense](r-intellisense.md), [lint](linting-r-code.md), [snippets de código](code-snippets-for-r.md), e [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Realce de sintaxe

Além de colorir diferentes partes do código, como cadeias de caracteres, comentários e palavras-chave, as RTVS também realçam e habilitam links em comentários:

![Coloração de sintaxe para código R](media/editing-syntax-colors.png)

Para personalizar fontes e certas cores de destaque, selecione o comando**Opções** **de ferramentas,** > navegue até**Fontes e Cores do** **Ambiente** > e altere as configurações para itens relacionados a R na caixa Itens de **exibição:**

![Opções de fontes e cores para código R](media/editing-syntax-colors-options.png)

O Visual Studio também sublinha erros de sintaxe no editor:

![Realce de erro de sintaxe no código R](media/editing-syntax-error.png)

Para alterar esse comportamento, consulte a**configuração de verificação de sintaxe** **avançada** > em [opções de editor](#editor-options).

## <a name="edit-and-organize-code"></a>Editar e organizar o código

Conforme você digita o código, as RTVS fornecem preenchimento automático, conforme descrito na página [IntelliSense](r-intellisense.md). Ele também faz a formatação automática, como o fechamento de chaves e parênteses:

![Animação de formatação embutida](media/editing-inline-formatting.gif)

Ao digitar chamadas de funções que têm muitos parâmetros, muitas vezes você deseja alinhar os parâmetros para deixar o código mais fácil de ler. As RTVS lembram do recuo que você definiu para os parâmetros e aplica esse recuo automaticamente às linhas subsequentes:

![Animação de recuo automático](media/editing-auto-indentation.gif)

Para alterar esse comportamento, consulte [opções do editor](#editor-options) e veja o grupo **Guias**.

As regiões de código recolhíveis permitem ocultar parte do código temporariamente no editor. O Visual Studio cria várias regiões para você automaticamente, como para declarações de várias linhas, a menos que a opção**Outlining** > **de delineamento** de código **avançado** > esteja definida como Descancelada.

Para criar uma região sua, coloque o código desejado entre comentários que terminam com `---`. Os controles pequenos +/- à esquerda do código permitem que você expanda e recolha regiões:

![Criando uma região recolhível com comentários](media/editing-collapsible-regions.gif)

Por padrão, o Visual Studio insere espaços quando você pressiona a tecla **Tab**. Novamente você pode alterar esse comportamento, conforme descrito em [Opções, Editor de Texto, Guias](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navegação de código

A navegação de código fornece acesso rápido ao código-fonte do seu programa do R e de suas bibliotecas. Esses recursos mantêm você no fluxo do seu trabalho em vez de precisar pesquisar manualmente o código.

**Ir para definição** rapidamente salta para uma definição de função ou um minieditor pop-up embutido para ler o código-fonte de uma função de biblioteca. Basta clicar com o botão direito do mouse na função de interesse e selecionar **Ir para Definição,** ou colocar o cursor na função e pressionar **F12**.

Este comando abre uma nova janela do editor que contém o código-fonte para a função. O cursor é convenientemente posicionado no início da definição de função.

**Peek Definition**, invocado a partir do menu com o botão direito do mouse ou **Alt**+**F12,** insere uma região rolável e somente leitura contendo o código-fonte da função abaixo da chamada de função:

![Animação para definição de espiada](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Enviar código para a janela interativa

Muitos desenvolvedores gostam escrever código no editor e, em seguida, enviá-lo para a [janela interativa](interactive-repl-for-r-in-visual-studio.md) para teste imediato [também conhecido como REPL (Read-Evaluate-Print-Loop)]. Pressionar **Ctrl**+**Enter** no editor R envia a linha de código atual para a janela interativa e, em seguida, coloca o cursor na próxima linha. Com **ctrl**+**Enter**, então, você pode efetivamente passar através de seu código a partir do editor.

Você também pode selecionar código e pressionar **Ctrl**+**Enter** para aplicar toda essa seleção. Como alternativa, clique com o botão direito do mouse na seleção e selecione **Executar em Interativo**.

## <a name="format-code"></a>Código de formatação

A formatação automática do Visual Studio mantém o código que você escreve, bem como o código que você cola no editor, formatados conforme definido por suas preferências. Você também pode fazer uma seleção, clicar com o botão direito do mouse e selecionar **Formatar Seleção** (**Ctrl**+**K**,**F**) para aplicar essas preferências. Por exemplo, se você tiver uma definição de função inteira em uma única linha:

```R
f<-function  (a){  return(a + 1) }
```

A aplicação da formatação a limpará deixando assim:

```R
f <- function(a) { return(a + 1) }
```

Para reformar todo o arquivo de código, selecione **Editar** > **documento de formato** **avançado** > **(Ctrl**+**E**,**D**).

A formatação automática é uma operação separada que pode ser desfeita. Por exemplo, se você colar código no editor e formatá-lo se aplica, selecionar **Editar** > **Desfazer** ou pressionar **Ctrl**+**Z** uma vez inverte a formatação; um segundo **Desfazer** inverte a pasta em si.

As opções de formatação (incluindo **Tools** > a formatação de desapartir) são definidas através de**opções de ferramentas** na guia Editor **de** > texto**R** > **Avançado.** Você pode ir diretamente para esta página usando o comando **R Tools** > **Editor opções** ou clicando com o botão direito do mouse no editor e selecionando **opções de formatação**. Consulte a seção de [opções do editor](#editor-options) para obter detalhes.

## <a name="inserting-roxygen-comments"></a>Inserindo comentários Roxygen

As RTVS fornecem um atalho para a geração de comentários [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) usando os nomes de parâmetro de uma função. Basta digitar `###` em uma linha em branco acima da definição de função:

![Animação da inserção de um comentário Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opções do editor

As opções específicas do editor são definidas através do comando **Ferramentas** > **Opções,** navegando para **o Editor de** > **texto R**ou usando o comando de atalho R **Ferramentas** > Editor**Options**.

As opções nas guias **Geral**, **Barras de rolagem** e **Guias** não são específicas para R, mas são configurações gerais do Visual Studio disponíveis para todas as linguagens, mas são aplicadas de acordo com cada linguagem. Para obter detalhes, confira os seguintes artigos:

- [Opções, Editor de Texto, Todas as Linguagens](../ide/reference/options-text-editor-all-languages.md)
- [Rastrear o código personalizando a barra de rolagem](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opções, editor de texto, guias](../ide/reference/options-text-editor-all-languages-tabs.md)

As opções na guia **R** > **Advanced** são específicas para RTVS:

| Agrupar | Opção | Padrão | Descrição |
| --- | --- | --- | --- |
| Formatação | Formatação automática | Por | Reformata o código enquanto você digita. Não afeta os comandos **Formatar Seleção** ou **Formatar Documento**. |
| | Chaves expandidas | Desativado | Coloca uma { aberta em uma nova linha. |
| | Formatar ao colar | Por | Aplica a formatação ao colar. |
| | Formatar escopo em } | Por | Formata o escopo depois de digitar uma } de fechamento. |
| | Espaço após a vírgula | Por | Coloca um espaço depois de vírgulas. |
| | Espaço após a palavra-chave | Por | Coloca um espaço depois de palavras-chave como `if`, `while` e `repeat`. |
| | Espaço antes de { | Por | Coloca um espaço antes de uma { de abertura. |
| | Espaços antes e depois de = | Por | Insere espaços antes e depois de um sinal de igual. |
| IntelliSense | Confirmar com a tecla Enter | Desativado | Confirma a seleção de preenchimento automático quando **Enter** é pressionado. |
| | Confirmar com a tecla Espaço | Desativado | Confirma a seleção de preenchimento automático quando **Espaço** é pressionado.|
| | Lista de conclusão no primeiro caractere | Por | Mostra a lista de conclusão nos primeiros tipos de caracteres. Quando desligado, uma lista de conclusão é exibida com **edit** > **intelliSense** > **List Members** **(Ctrl**+**J**). |
| | Lista de conclusão com a tecla **Tab** | Desativado | Invoca uma lista de conclusão digitando um ou mais caracteres e pressionando **Tab**. |
| | Corresponder parcialmente ao digitar nomes de argumento | Desativado | Ao digitar os nomes de argumento em uma chamada de função, a ajuda de assinatura mostra uma descrição do argumento que é a melhor correspondência. |
| Janela Interativa | Verificação de sintaxe no console do R | Desativado | Aplica a verificação na janela interativa de sintaxe. A verificação de sintaxe pode não funcionar corretamente com instruções de várias linhas. |
| Estrutura de tópicos | Estrutura de tópicos de código | Por | Cria regiões recolhíveis automaticamente para áreas como instruções de várias linhas. |
| Verificação de sintaxe | Mostrar erros de sintaxe | Por | Habilita a verificação de sintaxe automática do código. |
