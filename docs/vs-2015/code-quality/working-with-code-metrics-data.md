---
title: Trabalhando com dados de métricas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645702"
---
# <a name="working-with-code-metrics-data"></a>Trabalhando com dados de métricas de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela **resultados de métricas de código** exibe os dados gerados pela análise de métricas de código. Para obter mais informações sobre valores de dados de métricas de código, consulte [valores de métricas de código](../code-quality/code-metrics-values.md).

 Este tópico contém as seguintes seções:

- [Janela de resultados de métricas de código](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Exibindo resultados de métricas de código](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Filtrando resultados de métricas de código](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Adicionando, removendo e reorganizando colunas de dados](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Copiando dados para a área de transferência ou Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Criando um item de trabalho com base nos resultados da métrica de código](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="code-metrics-results-window"></a><a name="BKMK_CodeMetricsResultsWindow"></a> Janela de resultados de métricas de código
 A janela **resultados de métricas de código** tem uma barra de ferramentas na parte superior e colunas para exibir os resultados calculados.

|Coluna|Descrição|
|------------|-----------------|
|**Hierarquia**|A coluna **hierarquia** contém uma exibição de árvore da hierarquia de código que você pode expandir ou recolher para ver o nível de detalhe desejado. As colunas restantes mostram os resultados calculados. Você pode ocultar ou organizar as colunas de resultado como desejar.|
|**Facilidade de manutenção**|A coluna de **manutenção** contém um ícone além do resultado numérico. Um ícone verde indica um grau relativamente alto de manutenção. Um ícone amarelo indica um grau moderado de manutenção. Um ícone vermelho indica baixa capacidade de manutenção e um possível ponto de problema. Esses indicadores de cor correspondem às categorias de severidade usadas pela regra do FxCop AvoidUnmaintainableCode. Essa regra aciona um erro se o índice de manutenção for inferior a 10, um aviso se o índice estiver entre 10 e 20, e nem um erro nem um aviso se o índice for maior que 20. O índice de manutenção é uma síntese de três métricas: complexidade ciclomática, linhas de código e complexidade computacional. Seus valores não são expressos em unidades.|

## <a name="displaying-code-metrics-results"></a><a name="BKMK_DisplayingCodeMetricsResults"></a> Exibindo resultados de métricas de código
 A janela resultados de métricas de código é exibida automaticamente quando você gera resultados de métricas de código. Você também pode exibir a janela a qualquer momento.

#### <a name="to-display-the-code-metrics-results-window"></a>Para exibir a janela de resultados de métricas de código

- No menu **analisar** , clique em **Windows** e em **resultados de métricas de código**.

     \- ou –

- No menu **Exibir** , aponte para **outras janelas** e clique em **resultados de métricas de código**.

     A janela resultados de métricas de código é exibida mesmo quando não contém nenhum resultado.

#### <a name="to-view-code-metrics-details"></a>Para exibir detalhes de métricas de código

- Se os resultados de métricas de código tiverem sido gerados, expanda a árvore na coluna **hierarquia** .

## <a name="filtering-code-metrics-results"></a><a name="BKMK_FilteringCodeMetricsResults"></a> Filtrando resultados de métricas de código
 Você pode filtrar os resultados que são exibidos na janela **resultados de métricas de código** usando a barra de ferramentas na parte superior. Por exemplo, talvez você queira ver apenas os resultados que têm um índice de manutenção abaixo de 65.

 A caixa suspensa **filtro** contém os nomes das colunas de resultados. Quando um filtro é definido, ele é adicionado à parte inferior da lista, junto com um recuo. A lista pode conter os dez últimos filtros que foram definidos.

#### <a name="to-filter-the-code-metrics-results"></a>Para filtrar os resultados de métricas de código

1. Na lista **filtro** , selecione o nome da coluna.

2. Em **mín**., digite o valor mínimo a ser exibido.

3. Em **máximo**, digite o valor máximo a ser exibido.

4. Clique no botão **aplicar filtro** .

5. Para ver os detalhes do resultado, expanda a árvore hierarquia.

## <a name="adding-removing-and-rearranging-data-columns"></a><a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Adicionando, removendo e reorganizando colunas de dados
 Você pode adicionar ou remover colunas de resultados da janela **resultados de métricas de código** . Além disso, você pode reorganizar as colunas de resultados para que elas apareçam na ordem desejada.

#### <a name="to-remove-a-column"></a>Para remover uma coluna

1. Clique no botão **Adicionar/remover colunas** .

     \- ou –

     Clique com o botão direito do mouse em qualquer título de coluna e clique em **Adicionar/remover colunas**.

2. Na caixa de diálogo **Adicionar/remover colunas** , desmarque a caixa de seleção da coluna que você deseja remover e clique em **OK**.

#### <a name="to-add-a-previously-removed-column"></a>Para adicionar uma coluna removida anteriormente

1. Clique no botão **Adicionar/remover colunas** .

     \- ou –

     Clique com o botão direito do mouse em qualquer título de coluna e clique em **Adicionar/remover colunas**.

2. Na caixa de diálogo **Adicionar/remover colunas** , marque a caixa de seleção da coluna que você deseja adicionar e clique em **OK**.

#### <a name="to-rearrange-columns"></a>Para reorganizar colunas

1. Clique no botão **Adicionar/remover colunas** .

     \- ou –

     Clique com o botão direito do mouse em qualquer título de coluna e clique em **Adicionar/remover colunas**.

2. Na caixa de diálogo **Adicionar/remover colunas** , selecione a coluna que deseja mover e, em seguida, clique na seta para cima ou na seta para baixo.

3. Quando a coluna estiver posicionada onde você desejar, clique em **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a><a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Copiando dados para a área de transferência ou Excel
 Você pode selecionar e copiar uma linha selecionada de dados de métricas de código para a área de transferência como uma cadeia de texto que contém uma linha para o nome e o valor de cada coluna de dados. Você também pode clicar em **Abrir lista no Microsoft Excel** para exportar todos os resultados de métricas de código para uma planilha do Excel

## <a name="creating-a-work-item-based-on-code-metric-results"></a><a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Criando um item de trabalho com base nos resultados da métrica de código
 Você pode criar um [!INCLUDE[esprfound](../includes/esprfound-md.md)] item de trabalho com base nos resultados na janela **resultados da métrica de código** . Quando o item de trabalho é criado, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] insere automaticamente um título no campo **título** e os dados de métricas de código na guia **histórico** .

 Para obter mais informações sobre como criar itens de trabalho, consulte [criar um item de trabalho &#91;redirecionado&#93;](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>Para criar um item de trabalho com base em um resultado

1. Clique com o botão direito do mouse no resultado.

2. Aponte para **Criar item de trabalho**e clique no tipo de item de trabalho que você deseja criar (**bug**, **tarefa**e assim por diante).

3. Preencha o formulário de item de trabalho preenchendo todos os campos obrigatórios.

4. No menu **arquivo** , clique em **salvar tudo** para salvar o item de trabalho.

#### <a name="to-create-a-bug-based-on-a-result"></a>Para criar um bug com base em um resultado

1. Clique no resultado para selecioná-lo.

2. Clique no botão **Criar item de trabalho** .

3. Preencha o formulário de item de trabalho preenchendo todos os campos obrigatórios.

4. No menu **arquivo** , clique em **salvar tudo** para salvar o item de trabalho.

## <a name="see-also"></a>Consulte Também
 [Medindo a complexidade e a manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [como gerar dados de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
