---
title: Editar o código R
description: O Visual Studio fornece uma experiência de edição personalizada para R, mantendo todos os recursos e a capacidade de usar extensões.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 4aea7f5371dc425a77e10b64a9389571b06f80b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885853"
---
# <a name="edit-r-code-in-visual-studio"></a>Editar o código R no Visual Studio

As RTVS (Ferramentas do R para Visual Studio) personalizam a experiência de edição do Visual Studio especificamente para R, mantendo todos os recursos e a capacidade de usar extensões. (Por exemplo, se preferir associações de teclas VIM, será possível instalar a [extensão VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) gratuita do Visual Studio Marketplace.)

Além dos recursos neste artigo, veja também [IntelliSense](r-intellisense.md), [lint](linting-r-code.md), [snippets de código](code-snippets-for-r.md), e [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Realce de sintaxe

Além de colorir diferentes partes do código, como cadeias de caracteres, comentários e palavras-chave, as RTVS também realçam e habilitam links em comentários:

![Coloração de sintaxe para código R](media/editing-syntax-colors.png)

Para personalizar fontes e determinadas cores de realce, selecione o comando **ferramentas**  >  **Opções** , navegue até  >  **fontes e cores** do ambiente e altere as configurações dos itens relacionados ao R na caixa **Exibir itens** :

![Opções de fontes e cores para código R](media/editing-syntax-colors-options.png)

O Visual Studio também sublinha erros de sintaxe no editor:

![Realce de erro de sintaxe no código R](media/editing-syntax-error.png)

Para alterar esse comportamento, consulte a   >  configuração **verificação de sintaxe** avançada em opções do [Editor](#editor-options).

## <a name="edit-and-organize-code"></a>Editar e organizar o código

Conforme você digita o código, as RTVS fornecem preenchimento automático, conforme descrito na página [IntelliSense](r-intellisense.md). Ele também faz a formatação automática, como o fechamento de chaves e parênteses:

![Animação de formatação embutida](media/editing-inline-formatting.gif)

Ao digitar chamadas de funções que têm muitos parâmetros, muitas vezes você deseja alinhar os parâmetros para deixar o código mais fácil de ler. As RTVS lembram do recuo que você definiu para os parâmetros e aplica esse recuo automaticamente às linhas subsequentes:

![Animação de recuo automático](media/editing-auto-indentation.gif)

Para alterar esse comportamento, consulte [opções do editor](#editor-options) e veja o grupo **Guias**.

As regiões de código recolhíveis permitem ocultar parte do código temporariamente no editor. O Visual Studio cria várias regiões para você automaticamente, como para instruções de várias linhas, a menos que a opção de estrutura de código de estrutura de tópicos **avançada**  >    >   esteja definida como off.

Para criar uma região sua, coloque o código desejado entre comentários que terminam com `---`. Os controles pequenos +/- à esquerda do código permitem que você expanda e recolha regiões:

![Criando uma região recolhível com comentários](media/editing-collapsible-regions.gif)

Por padrão, o Visual Studio insere espaços quando você pressiona a tecla **Tab**. Novamente você pode alterar esse comportamento, conforme descrito em [Opções, Editor de Texto, Guias](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navegação de código

A navegação de código fornece acesso rápido ao código-fonte do seu programa do R e de suas bibliotecas. Esses recursos mantêm você no fluxo do seu trabalho em vez de precisar pesquisar manualmente o código.

**Ir para definição** rapidamente salta para uma definição de função ou um minieditor pop-up embutido para ler o código-fonte de uma função de biblioteca. Basta clicar com o botão direito do mouse na função de interesse e selecionar **ir para definição**, ou posicionar o cursor na função e pressionar **F12**.

Este comando abre uma nova janela do editor que contém o código-fonte para a função. O cursor é convenientemente posicionado no início da definição de função.

A **definição de inspeção**, invocada no menu do botão direito do mouse ou **ALT** + **F12**, insere uma região somente leitura e rolável contendo o código-fonte da função abaixo da chamada de função:

![Animação para definição de espiada](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Enviar código para a janela interativa

Muitos desenvolvedores gostam escrever código no editor e, em seguida, enviá-lo para a [janela interativa](interactive-repl-for-r-in-visual-studio.md) para teste imediato [também conhecido como REPL (Read-Evaluate-Print-Loop)]. Pressionar **Ctrl** + **Enter** no editor de R envia a linha de código atual para a janela interativa e, em seguida, coloca o cursor na linha seguinte. Com **Ctrl** + **Enter**, você pode efetivamente percorrer seu código no editor.

Você também pode selecionar o código e pressionar **Ctrl** + **Enter** para aplicar a seleção inteira. Como alternativa, clique com o botão direito do mouse na seleção e selecione **Executar em Interativo**.

## <a name="format-code"></a>Código de formatação

A formatação automática do Visual Studio mantém o código que você escreve, bem como o código que você cola no editor, formatados conforme definido por suas preferências. Você também pode fazer uma seleção, clicar com o botão direito do mouse e selecionar **Formatar Seleção** (**Ctrl**+**K**,**F**) para aplicar essas preferências. Por exemplo, se você tiver uma definição de função inteira em uma única linha:

```R
f<-function  (a){  return(a + 1) }
```

A aplicação da formatação a limpará deixando assim:

```R
f <- function(a) { return(a + 1) }
```

Para reformatar o arquivo de código inteiro, selecione **Editar**  >  documento de  >  **formato** avançado (**Ctrl** + **E**,**D**).

A formatação automática é uma operação separada que pode ser desfeita. Por exemplo, se você colar o código no editor e a formatação aplicável, selecionar **Editar**  >  **desfazer** ou pressionar **Ctrl** + **Z** uma vez reverte a formatação; uma segunda **desfazer** inverte a colagem em si.

As opções de formatação (incluindo a desativação da formatação) são definidas por meio de **ferramentas**  >  **Opções** na   >    >  guia **avançado** do editor de texto. Você pode ir diretamente para esta página usando o comando opções do editor de **Ferramentas do R**  >   ou clicando com o botão direito do mouse no editor e selecionando **Opções de formatação**. Consulte a seção de [opções do editor](#editor-options) para obter detalhes.

## <a name="inserting-roxygen-comments"></a>Inserindo comentários Roxygen

As RTVS fornecem um atalho para a geração de comentários [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) usando os nomes de parâmetro de uma função. Basta digitar `###` em uma linha em branco acima da definição de função:

![Animação da inserção de um comentário Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opções do editor

As opções específicas do editor são definidas por meio do comando opções de **ferramentas**  >   , navegando até o **Editor de texto**  >  **R** ou usando o comando de atalho opções do editor de **ferramentas R**  >  .

As opções nas guias **Geral**, **Barras de rolagem** e **Guias** não são específicas para R, mas são configurações gerais do Visual Studio disponíveis para todas as linguagens, mas são aplicadas de acordo com cada linguagem. Para obter detalhes, confira os seguintes artigos:

- [Opções, Editor de Texto, Todas as Linguagens](../ide/reference/options-text-editor-all-languages.md)
- [Rastrear o código personalizando a barra de rolagem](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opções, editor de texto, guias](../ide/reference/options-text-editor-all-languages-tabs.md)

As opções na guia de **R**  >  **Advanced** são específicas para RTVS:

| Grupo | Opção | Padrão | Descrição |
| --- | --- | --- | --- |
| Formatação | Formatação automática | Ativado | Reformata o código enquanto você digita. Não afeta os comandos **Formatar Seleção** ou **Formatar Documento**. |
| | Chaves expandidas | Desativado | Coloca uma { aberta em uma nova linha. |
| | Formatar ao colar | Ativado | Aplica a formatação ao colar. |
| | Formatar escopo em } | Ativado | Formata o escopo depois de digitar uma } de fechamento. |
| | Espaço após a vírgula | Ativado | Coloca um espaço depois de vírgulas. |
| | Espaço após a palavra-chave | Ativado | Coloca um espaço depois de palavras-chave como `if`, `while` e `repeat`. |
| | Espaço antes de { | Ativado | Coloca um espaço antes de uma { de abertura. |
| | Espaços antes e depois de = | Ativado | Insere espaços antes e depois de um sinal de igual. |
| IntelliSense | Confirmar com a tecla Enter | Desativado | Confirma a seleção de preenchimento automático quando **Enter** é pressionado. |
| | Confirmar com a tecla Espaço | Desativado | Confirma a seleção de preenchimento automático quando **Espaço** é pressionado.|
| | Lista de conclusão no primeiro caractere | Ativado | Mostra a lista de conclusão nos primeiros tipos de caracteres. Quando desativado, uma lista de conclusão é exibida com a opção **Editar**  >    >  **membros da lista** do IntelliSense (**Ctrl** + **J**). |
| | Lista de conclusão com a tecla **Tab** | Desativado | Invoca uma lista de conclusão digitando um ou mais caracteres e pressionando **Tab**. |
| | Corresponder parcialmente ao digitar nomes de argumento | Desativado | Ao digitar os nomes de argumento em uma chamada de função, a ajuda de assinatura mostra uma descrição do argumento que é a melhor correspondência. |
| Janela Interativa | Verificação de sintaxe no console do R | Desativado | Aplica a verificação na janela interativa de sintaxe. A verificação de sintaxe pode não funcionar corretamente com instruções de várias linhas. |
| Estrutura de tópicos | Estrutura de tópicos de código | Ativado | Cria regiões recolhíveis automaticamente para áreas como instruções de várias linhas. |
| Verificação de sintaxe | Mostrar erros de sintaxe | Ativado | Habilita a verificação de sintaxe automática do código. |
