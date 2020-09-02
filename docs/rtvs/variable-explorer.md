---
title: Gerenciador de Variáveis para R
description: O Gerenciador de Variáveis no Visual Studio mostra todas as variáveis em um determinado escopo na sessão atual de R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 799b7f2789898e0d02d9588f9a3ad7d1e8098a00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62809768"
---
# <a name="variable-explorer"></a>Gerenciador de Variáveis

A janela **Gerenciador de Variáveis**, aberta com **Ferramentas do R** > **Janelas** > **Gerenciador de Variáveis** (ou **Ctrl**+**8** se você já usou **Ferramentas do R** > **Configurações da Ciência de Dados**), mostra todas as variáveis em determinado escopo na sessão atual do R. Por exemplo, se você abrir o **Gerenciador de Variáveis** e inserir as seguintes linhas na [janela interativa](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Em seguida, a janela **Gerenciador de Variáveis** será exibida da seguinte maneira:

![Janela do Gerenciador de Variáveis no Visual Studio](media/variable-explorer-window.png)

Se você tiver um quadro de dados R mais complexo definido na sessão, será possível navegar nos dados. Por exemplo, após a execução de `cars <- mtcars`, percorra o conjunto de dados expandindo os diferentes nós no **Gerenciador de Variáveis**:

![Exibição expandida do Gerenciador de Variáveis](media/variable-explorer-expanded-results.png)

Para excluir variáveis, clique com o botão direito do mouse e selecione **Excluir** ou selecione a variável e pressione a tecla **Delete**.

Você também pode procurar uma observação em um quadro de dados usando a pesquisa incremental. Primeiro, expanda os nós no quadro de dados que deseja pesquisar e insira os termos de pesquisa na caixa de pesquisa.

## <a name="details-table-view"></a>Exibição de detalhes (tabela)

Como os dados costumam ser tabulares, você pode exibir qualquer tipo de dados complexo como uma tabela separada, selecionando o ícone de lupa ou clicando com o botão direito do mouse e selecionando **Mostrar Detalhes**.

![Exibição de tabela do Gerenciador de Variáveis](media/variable-explorer-table-view.png)

Clicar em um título de coluna classifica os dados pela coluna (alternando entre crescente e decrescente). Manter pressionada a **tecla Shift** e clicar em colunas adicionais adiciona essas colunas também à classificação. Se você clicar em uma coluna sem pressionar a tecla **Shift**, retornará para a classificação de coluna única.

A sequência em que você clica nos títulos de coluna determina a ordem na qual a classificação é executada. Por exemplo, pressione **Shift** + e**clique** na coluna **cyl** e, em seguida, **Shift** + **clique** na coluna **MPG** duas vezes para classificar a lista para cilindros crescentes e decrescente de milhas por litro:

![Exibição de tabela de classificação de dados por duas colunas.](media/variable-explorer-table-view-sorting.png)

Como o **Gerenciador de Variáveis** e as exibições de tabela estão em janelas separadas do Visual Studio, você pode organizá-las conforme desejar para o trabalho lado a lado. Consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) para obter instruções gerais.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Abrir no Excel (ou em outro aplicativo compatível com CSV)

Para manipulação adicional e análise, geralmente é útil exportar as variáveis de sessão para CSV. A exportação é feita com o pequeno ícone do Excel ( ![ ícone de exportação do Excel ](media/variable-explorer-excel-icon.png) ) ao lado de cada nó na **Gerenciador de variáveis**ou clicando com o botão direito do mouse em um item e selecionando **abrir no aplicativo CSV**. A seleção do ícone grava os dados em um novo arquivo CSV na pasta *%userprofile%\Documents\RTVS_CSV_Exports* e, em seguida, inicia esse arquivo, que o abre em qualquer outro aplicativo associado à extensão *.csv*.

## <a name="scopes"></a>Escopos

Por padrão, o **Gerenciador de Variáveis** é aberto no escopo global. Você pode mudar para um escopo de pacote, selecionando um pacote no menu suspenso na parte superior da janela.

![Gerenciador de Variáveis mostrando um escopo de pacote](media/variable-explorer-package-scopes.png)

Você também pode alternar para um escopo de função quando interrompido em um ponto de interrupção no depurador (Observe que **Gerenciador de variáveis** não alterna automaticamente para o escopo de função do código que está sendo depurado):

![Gerenciador de Variáveis mostrando um quadro de dados durante a depuração](media/variable-explorer-as-locals-window.png)

O **Gerenciador de Variáveis** altera o escopo de função automaticamente conforme você executa o código em etapas no depurador, como a exibição de variáveis locais em uma função.

## <a name="import-data-into-variable-explorer"></a>Importar dados para o Gerenciador de Variáveis

Dois comandos na barra de ferramentas do **Gerenciador de Variáveis**, que também estão disponíveis no menu **Ferramentas do R** > **Dados**, importam conjuntos de dados CSV externos para a sessão do R: **Importar conjunto de dados para a sessão do R por meio de uma URL da Web** e **Importar conjunto de dados para a sessão do R por meio de um arquivo de texto**.

Depois de identificar o arquivo CSV a ser importado, o Visual Studio exibe uma caixa de diálogo **Importar Conjunto de Dados**, na qual há opções para controlar como esse arquivo de dados é analisado (ou seja, o que é o separador de campo e como lidar com aspas). Você também pode ver uma versão prévia do quadro de dados importado e do arquivo de dados original:

![Caixa de diálogo Importar conjunto de dados](media/variable-explorer-import-dataset-dialog.png)
