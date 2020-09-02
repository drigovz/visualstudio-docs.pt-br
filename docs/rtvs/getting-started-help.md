---
title: Janela de Ajuda para R
description: A ajuda do R está integrada diretamente na janela interativa no Visual Studio por meio do comando ? .
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62950588"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Ajuda nas Ferramentas do R para Visual Studio

A ajuda do R está integrada diretamente na janela interativa no Visual Studio. Sempre que você usar o comando `?`, como `?mtcars`, a ajuda da documentação do R aparecerá em uma janela do Visual Studio:

![janela da Ajuda no Visual Studio](media/help-window.png)

> [!Tip]
> A janela da Ajuda, como todas as outras no Visual Studio, pode ser organizada e encaixada conforme o desejado. Consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Para abrir os resultados da ajuda em um navegador, selecione o menu de opções das **Ferramentas do R**  >  **Options** e defina a propriedade **ajuda do R navegador** como `External` . Consulte [Opções](options-for-r-tools-in-visual-studio.md).

Para pesquisar a ajuda, use o comando `??` seguido por um termo de pesquisa. Use aspas se o termo de pesquisa contiver espaços:

```R
??"Motor Trend"
```

![Resultados da pesquisa da ajuda](media/help-search1.png)

A janela da Ajuda também tem um campo de entrada de pesquisa por meio do qual você pode realizar mais pesquisas diretamente na documentação do R:

![Resultados da pesquisa da ajuda usando o campo de entrada](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Pesquisa da ajuda integrada

Os desenvolvedores geralmente pesquisam a documentação do R para obter ajuda sobre nomes de função, conjuntos de dados e outros elementos. As RTVS (Ferramentas do R para Visual Studio) simplificam o processo integrando as pesquisas de ajuda às janelas de editor e interativa.

- Pressionar **F1** durante uma operação de preenchimento automático produz uma lista de resultados da ajuda que correspondem à subcadeia de caracteres.
- Clicar com o botão direito do mouse em um termo de pesquisa (como uma função) e selecionar o comando **Ajuda sobre** abre a ajuda para essa função. Você também pode invocar **Ajuda sobre** para qualquer seleção.

    ![Invocando a ajuda por meio do menu de contexto acionado com um clique no botão direito do mouse](media/help-right-click.png)

> [!Tip]
> Para abrir a ajuda integrada em um navegador, **R Tools**selecione  >  **Opções** de ferramentas de R e defina o **navegador da Web F1** como `External` . Consulte [Opções](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Pesquisa integrada do StackOverflow

Além de pesquisar na documentação do R, os desenvolvedores geralmente pesquisam no StackOverflow enquanto escrevem o código. As RTVS simplificam o processo. Clique com o botão direito do mouse em um termo ou uma seleção, selecione o comando **Pesquisar na Web** (**Ctrl** + **F1**) e o Visual Studio abre uma janela com os resultados da pesquisa com escopo para StackOverflow:

![Resultados da pesquisa da Web no Visual Studio](media/help-web-search-results.png)

Você pode alterar a cadeia de caracteres de escopo acrescentada, `R site:stackoverflow` , por meio das opções de **Ferramentas do R**  >  **Options**  >  opção**F1 de cadeia de pesquisa da Web** :

![Alterando a opção de cadeia de pesquisa da Web F1](media/options-dialog.png)

Se você preferir exibir os resultados em um navegador, altere a opção **Navegador da Web F1** conforme descrito em [Opções](options-for-r-tools-in-visual-studio.md).