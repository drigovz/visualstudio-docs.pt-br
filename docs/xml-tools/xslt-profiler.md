---
title: Desempenho do XSLT
description: Saiba mais sobre o XSLT Profiler no Visual Studio que cria relatórios de desempenho XSLT detalhados para ajudá-lo a otimizar o desempenho do seu código XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/11/2020
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: f2214ab4d66dcad1ee92eda7d7acbb94b89e8eb6
ms.sourcegitcommit: 83a39d48b00c6c351e5c1707942633b7f73aaad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94531882"
---
# <a name="the-xslt-profiler"></a>O criador de perfil XSLT

O profiler XSLT criar relatórios de desempenho detalhados XSLT que a medida da ajuda, avalia, e problemas de desempenho relacionados de destino no código XSLT. O profiler XSLT inclui dicas úteis para XSL e otimizações de folha de estilos XSLT. Para aplicativos que requerem XSLT máximo desempenho, essa ferramenta pode ser essencial.

O XSLT Profiler faz parte do Visual Studio e está disponível no menu **XML** .

![Criador de perfil XSLT](../xml-tools/media/profile-xslt-menu.png "Captura de tela dos itens de menu XML no Visual Studio 2017")

> [!NOTE]
> O XSLT Profiler só está disponível na edição Enterprise do Visual Studio 2017.

## <a name="create-a-performance-report"></a>Criar um relatório de desempenho

1. Abra um documento XSLT no Visual Studio 2017.

2. Na barra de menus, escolha **XML**  >  **XSLT de perfil** XML.

3. Fornecer um documento XML de entrada. Se um documento XML ele já não estiver aberto, você será solicitado para o arquivo.

   Inicia a análise, e uma barra de progresso exibem o progresso no editor. A saída XSLT também é visível.

4. Após a conclusão da sessão de desempenho, verifique o relatório de desempenho para analisar o desempenho do XSLT.

## <a name="get-all-available-views"></a>Obter todas as exibições disponíveis

1. Clique na lista suspensa **exibição atual** para obter todas as exibições disponíveis.

2. Selecione a opção **modo de exibição de resumo** na lista suspensa **exibição atual** . Por padrão, um relatório de desempenho é exibido na **exibição de resumo**. Esta exibição é um ponto de partida para determinar problemas de desempenho com documentos XSLT. A **exibição de resumo** lista os seguintes pontos de dados:

   - A maioria chamaram funções

   - Funções com a maioria de trabalho individual

   - Funções que usam o tempo os mais longa de executar

   Por padrão, há três colunas para cada ponto de dados: o nome da função, o número de chamadas o valor absoluto, e um valor percentual de função chamado para chamadas de função total. De cada ponto de dados na **exibição de resumo** , você pode navegar para exibições mais detalhadas clicando com o botão direito do mouse nos pontos de dados da função.

3. Selecione a opção de **exibição de função** na lista suspensa **exibição atual** . A **exibição de função** lista as funções chamadas durante a criação de perfil. Você pode classificar os dados em um nome de coluna. As colunas exibidas por padrão são:

    - **Nome da função**

    - **Tempo Inclusivo Decorrido**

    - **Tempo Exclusivo Decorrido**

    - **Tempo Inclusivo do Aplicativo**

    - **Tempo Exclusivo do Aplicativo**

    - **Número de Chamadas**

   Todas as colunas de tempo são exibidas em valores absolutos e em porcentagens. O termo **exclusivo** refere-se ao tempo total que uma função gastou em execução exclusiva de tempo gasto por outras funções chamadas durante a execução dessa função.

   O termo **inclusivo** refere-se ao tempo total que uma função gastou executando, incluindo o tempo de execução de todas as funções que ele chamou e se alguma delas chamou funções chamadas de outras funções.

## <a name="select-callercallee-view"></a>O modo de seleção do chamador/receptor

Selecione o modo de exibição **chamador/receptor** na lista suspensa **exibição atual** . O modo de exibição **chamador/receptor** tem as três partes distintas a seguir:

- **Funções que chamaram** : todas as funções que chamaram uma função específica são listadas na parte superior da exibição.

- **Função atual** : a função específica que foi chamada está listada na parte intermediária do modo de exibição.

- **Funções que foram chamadas por** : todas as funções que foram chamadas pela função específica são listadas na parte inferior da exibição.

Se uma função chamada `SyncToNavigator` aparece na parte média de exibição, todas as funções que chamaram a função de `SyncToNavigator` aparecem na parte superior de exibição, e em todas as funções que foram chamados por `SyncToNavigator` aparecem na parte de fundo de exibição.

- Você pode alterar a função na parte média de exibição clicando duas vezes em algumas das funções listadas em duas outras partes de exibição. A exibição é atualizado para refletir automaticamente as alterações.

- Você também pode classificar os dados clicando em nomes de coluna.

## <a name="select-call-tree-view"></a>Selecionar exibição de árvore de chamada

- Selecione **modo de exibição de árvore de chamada** na lista suspensa **exibição atual** . Esta exibição é um modo de exibição de árvore de execução do programa.

   O **modo de exibição de árvore de chamadas** mostra a raiz da árvore como o nome do processo. As funções são os nós de árvore. Esta exibição permite que você fure em rastreamentos específicos de chamada e analise que os rastreamentos têm o maior impacto de desempenho. A exibição é semelhante à **exibição da pilha de chamadas** disponível durante a depuração. Além das colunas no **modo de exibição de função** , no modo de exibição de árvore de **chamada** , há uma coluna adicional para exibir o **nome do módulo**.

- Selecione **marcas** na lista suspensa **exibição atual** .

   Com o XSLT Profiler, há marcas que aparecem no fluxo de coleta de dados com um comentário associado. As marcas são locais no código que têm contadores. Quando você indica que o profiler XSLT para coletar contadores de desempenho XSLT, os contadores obtém como cada vez que uma dessas marcas é executado. Os dados são exibidos em uma tabela que contém a **ID de marca** , o nome da **marca** ( **Iniciar programa** , **encerrar programa** ) e o **carimbo de data/hora**. As marcas não são agregadas e aparecem em ordem cronológica na exibição de **marcas** do relatório de desempenho.

## <a name="select-modules-in-the-current-view"></a>Módulos selecionados na exibição atual

- Selecione **módulos** na lista suspensa **exibição atual** .

   Exibição de módulos é uma lista plana das funções agregadas para o nível de módulo. Expandir ou recolher o nome do módulo para exibir ou fechar a exibição de dados de desempenho do módulo. Você pode classificar os dados em um nome de coluna. Por padrão, há valores absolutos e números percentuais para **tempo inclusivo decorrido** , **tempo exclusivo decorrido** , **tempo inclusivo do aplicativo** , **tempo exclusivo do aplicativo** e **número de chamadas**.

- Selecione **processar** na lista suspensa **exibição atual** .

   A exibição processo exibe uma tabela que inclui a **ID do processo** , o **nome do processo** , a hora de **início** e a **hora de término**. Os dados podem ser classificados clicando em nomes de coluna.

## <a name="see-also"></a>Confira também

- [Walkthrough: usando a hierarquia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
