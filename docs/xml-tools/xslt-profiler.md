---
title: Desempenho do XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ecc5482c8519ceadfe1e6d5db7880c98b3d2ceb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525473"
---
# <a name="the-xslt-profiler"></a>O Profiler XSLT

O profiler XSLT criar relatórios de desempenho detalhados XSLT que a medida da ajuda, avalia, e problemas de desempenho relacionados de destino no código XSLT. O profiler XSLT inclui dicas úteis para XSL e otimizações de folha de estilos XSLT. Para aplicativos que requerem XSLT máximo desempenho, essa ferramenta pode ser essencial.

O Profiler XSLT é parte do Visual Studio e está disponível na **XML** menu.

![Perfil XSLT](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> O Profiler XSLT só está disponível na edição Enterprise do Visual Studio.

## <a name="create-a-performance-report"></a>Criar um relatório de desempenho

1. Abrir um documento XSLT no Visual Studio.

2. Na barra de menus, escolha **XML** > **perfil XSLT**.

3. Fornecer um documento XML de entrada. Se um documento XML ele já não estiver aberto, você será solicitado para o arquivo.

   Inicia a análise, e uma barra de progresso exibem o progresso no editor. A saída XSLT também é visível.

4. Após o término da sessão de desempenho, verifique o relatório de desempenho para analisar o desempenho do XSLT.

## <a name="get-all-available-views"></a>Obter todos os modos de exibição disponíveis

1. Clique no **modo de exibição atual** lista suspensa para obter todos os modos de exibição disponíveis.

2. Selecione o **modo de exibição de resumo** opção a **modo de exibição atual** lista suspensa. Por padrão, um relatório de desempenho é exibido na **modo de exibição resumo**. Esta exibição é um ponto de partida para determinar problemas de desempenho com documentos XSLT. O **modo de exibição resumo** relaciona os pontos de dados a seguir:

   - A maioria chamaram funções

   - Funções com a maioria de trabalho individual

   - Funções que usam o tempo os mais longa de executar

   Por padrão, há três colunas para cada ponto de dados: o nome da função, o número de chamadas o valor absoluto, e um valor percentual de função chamado para chamadas de função total. De cada data point-in a **modo de exibição de resumo**, você pode navegar para exibições mais detalhadas clicando nos pontos de dados de função.

3. Selecione o **exibição da função** opção a **modo de exibição atual** lista suspensa. O **exibição da função** lista funções chamadas durante a criação de perfil. Você pode classificar os dados em um nome de coluna. As colunas exibidas por padrão são:

    - **Nome da Função**

    - **Tempo Inclusivo Decorrido**

    - **Tempo Exclusivo Decorrido**

    - **Tempo Inclusivo do Aplicativo**

    - **Tempo Exclusivo do Aplicativo**

    - **Número de Chamadas**

   Todas as colunas de tempo são exibidas em valores absolutos e em porcentagens. O termo **exclusivo** refere-se ao tempo total de uma função executar gasta não incluem o tempo gasto por outras funções chamado durante a execução dessa função.

   O termo **inclusivo** refere-se ao tempo total gasto em execução, incluindo o tempo de execução de todas as funções que chamou e se qualquer uma das funções chamados chamaram outras funções.

## <a name="select-callercallee-view"></a>O modo de seleção do chamador/receptor

Selecione **chamador/receptor** exibir na **modo de exibição atual** lista suspensa. O **chamador/receptor** exibição tem três partes distintas:

- **Funções que chamaram**: Todas as funções que chamaram uma função particular são listadas na parte superior do modo de exibição.

- **Função atual**: A função específica que foi chamada é listada na parte do meio da exibição.

- **Funções que foram chamadas pela**: Todas as funções que foram chamadas pela função particular são listadas na parte inferior do modo de exibição.

Se uma função chamada `SyncToNavigator` aparece na parte média de exibição, todas as funções que chamaram a função de `SyncToNavigator` aparecem na parte superior de exibição, e em todas as funções que foram chamados por `SyncToNavigator` aparecem na parte de fundo de exibição.

- Você pode alterar a função na parte média de exibição clicando duas vezes em algumas das funções listadas em duas outras partes de exibição. A exibição é atualizado para refletir automaticamente as alterações.

- Você também pode classificar os dados clicando em nomes de coluna.

## <a name="select-call-tree-view"></a>Selecione o modo de exibição de árvore de chamada

- Selecione **modo de exibição de árvore de chamadas** na **modo de exibição atual** lista suspensa. Esta exibição é um modo de exibição de árvore de execução do programa.

   O **modo de exibição de árvore de chamadas** mostra a raiz da árvore como o nome do processo. As funções são os nós de árvore. Esta exibição permite que você fure em rastreamentos específicos de chamada e analise que os rastreamentos têm o maior impacto de desempenho. A exibição é semelhante a **modo de exibição de pilha de chamadas** disponível durante a depuração. Além das colunas na **exibição da função**, no **modo de exibição de árvore de chamadas**, há uma coluna adicional para exibir o **nome do módulo**.

- Selecione **marcas** na **modo de exibição atual** lista suspensa.

   Com o Profiler XSLT, há marcas que aparecem no fluxo de coleta de dados com um comentário associado. As marcas são locais no código que têm contadores. Quando você indica que o profiler XSLT para coletar contadores de desempenho XSLT, os contadores obtém como cada vez que uma dessas marcas é executado. Os dados são exibidos em uma tabela que contém o **ID de marca**, **nome da marca** (**Iniciar programa**, **finalizar programa**) e o  **Time Stamp**. As marcas não são agregadas e exibidos em ordem cronológica na **exibição de marcas** de relatório de desempenho.

## <a name="select-modules-in-the-current-view"></a>Módulos selecionados na exibição atual

- Selecione **módulos** na **modo de exibição atual** lista suspensa.

   Exibição de módulos é uma lista plana das funções agregadas para o nível de módulo. Expandir ou recolher o nome do módulo para exibir ou fechar a exibição de dados de desempenho do módulo. Você pode classificar os dados em um nome de coluna. Por padrão, há valores absolutos e números de porcentagem para **tempo incluindo decorridos**, **tempo exclusivo decorrido**, **tempo inclusivo do aplicativo**, **Tempo exclusivo do aplicativo**, e **número de chamadas**.

- Selecione **processo** na **modo de exibição atual** lista suspensa.

   A exibição processo exibe uma tabela que inclui o **ID do processo**, **nome do processo**, **inicie tempo**e o **hora de término**. Os dados podem ser classificados clicando em nomes de coluna.

## <a name="see-also"></a>Consulte também

- [Passo a passo: Usando a hierarquia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)