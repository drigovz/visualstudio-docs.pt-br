---
title: Janela de métricas de código
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126360a5cbc39653405d83362ae150edba401fb8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448697"
---
# <a name="use-the-code-metrics-results-window"></a>Usar a janela de resultados de métricas de código

A janela **resultados de métricas de código** exibe os dados gerados pela análise de métricas de código. Para obter mais informações sobre valores de dados de métricas de código, consulte [valores de métricas de código](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Exibir resultados de métricas de código

A janela **resultados de métricas de código** é exibida automaticamente quando você gera resultados de métricas de código. Você também pode exibir a janela a qualquer momento.

Você pode exibir a janela de resultados de métricas de código usando uma das seguintes sequências de menu:

- No menu **analisar** , escolha**resultados de métricas de código**do **Windows** > .

- No menu **Exibir** , escolha outros**resultados de métricas de código**do **Windows** > .

A janela **resultados de métricas de código** é aberta, mesmo que não contenha nenhum resultado.

### <a name="to-view-code-metrics-details"></a>Para exibir detalhes de métricas de código

Se os resultados de métricas de código tiverem sido gerados, expanda a árvore na coluna **hierarquia** .

## <a name="filter-code-metrics-results"></a>Filtrar resultados de métricas de código

Você pode filtrar os resultados que são exibidos na janela **resultados de métricas de código** usando a barra de ferramentas na parte superior. Por exemplo, talvez você queira ver apenas os resultados que têm um índice de manutenção abaixo de 65.

A caixa suspensa **filtro** contém os nomes das colunas de resultados. Quando um filtro é definido, ele é adicionado à parte inferior da lista, junto com um recuo. A lista pode conter os 10 últimos filtros que foram definidos.

### <a name="to-filter-the-code-metrics-results"></a>Para filtrar os resultados de métricas de código

1. Na lista **filtro** , selecione o nome da coluna.

2. Em **mín**., digite o valor mínimo a ser exibido.

3. Em **máximo**, digite o valor máximo a ser exibido.

4. Clique no botão **aplicar filtro** .

5. Para ver os detalhes do resultado, expanda a árvore hierarquia.

## <a name="add-remove-and-rearrange-data-columns"></a>Adicionar, remover e reorganizar colunas de dados

Você pode adicionar ou remover colunas de resultados da janela **resultados de métricas de código** . Além disso, você pode reorganizar as colunas de resultados para que elas apareçam na ordem desejada.

### <a name="add-or-remove-a-column"></a>Adicionar ou remover uma coluna

1. Clique no botão **Adicionar/remover colunas** ou clique com o botão direito do mouse em qualquer título de coluna e clique em **Adicionar/remover colunas**.

1. Na caixa de diálogo **Adicionar/remover colunas** , marque ou desmarque a caixa de seleção da coluna que você deseja adicionar ou remover e, em seguida, escolha **OK**.

### <a name="rearrange-columns"></a>Reorganizar colunas

1. Clique no botão **Adicionar/remover colunas** .

1. Na caixa de diálogo **Adicionar/remover colunas** , selecione a coluna que você deseja mover e escolha a seta para cima ou para baixo.

1. Quando a coluna estiver posicionada onde você desejar, escolha **OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Copiar dados para a área de transferência ou Excel

Você pode selecionar e copiar uma linha selecionada de dados de métricas de código para a área de transferência como uma cadeia de texto que contém uma linha para o nome e o valor de cada coluna de dados. Você também pode clicar em **abrir seleção no Microsoft Excel** para exportar todos os resultados de métricas de código para uma planilha do Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Criar um item de trabalho com base nos resultados da métrica de código

Você pode criar um [Azure boards](/azure/devops/boards/index?view=vsts) item de trabalho com base nos resultados na janela **resultados da métrica de código** . Quando o item de trabalho é criado, o Visual Studio insere automaticamente um título no campo **título** e dados de métricas de código na guia **histórico** .

Para obter mais informações sobre Azure Boards itens de trabalho, consulte [itens de trabalho](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Para criar um item de trabalho com base em um resultado

1. Clique com o botão direito do mouse no resultado.

2. Aponte para **Criar item de trabalho**e clique no tipo de item de trabalho que você deseja criar (**bug**, **tarefa**e assim por diante).

3. Preencha o formulário de item de trabalho preenchendo todos os campos obrigatórios.

4. No menu **arquivo** , clique em **salvar tudo** para salvar o item de trabalho.

### <a name="to-create-a-bug-based-on-a-result"></a>Para criar um bug com base em um resultado

1. Clique no resultado para selecioná-lo.

2. Clique no botão **Criar item de trabalho** .

3. Preencha o formulário de item de trabalho preenchendo todos os campos obrigatórios.

4. No menu **arquivo** , clique em **salvar tudo** para salvar o item de trabalho.

## <a name="see-also"></a>Consulte também

- [Valores de métricas de código](../code-quality/code-metrics-values.md)
- [Como gerar dados de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
