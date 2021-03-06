---
title: Coletar dados de amostragem no nível de linha | Microsoft Docs
description: Saiba como a amostragem de nível de linha do criador de perfil pode revelar o código que usa grandes quantidades de tempo do processador. Ele funciona com código gerenciado e nativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 222ba8cd5eb8e45be368d70c204a7c7c76b1a3e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886256"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Como coletar dados de amostragem no nível de linha
A amostragem de nível de linha é a capacidade do criador de perfil para determinar o local no código de uma função de processamento intensivo em que o processador tem que gastar a maior parte de seu tempo, como uma função que tem amostras altamente exclusivas.

## <a name="overview"></a>Visão geral
 Para amostragem de nível de linha, o criador de perfil percorre a pilha de chamadas do programa em intervalos definidos e agrega os resultados. Esses resultados mostram quais instruções o processador estava executando quando as amostras foram obtidas. Em seguida, os dados coletados sobre amostras exclusivas são analisados para identificar as linhas de código e o IP (ponteiro de instrução).

 A amostragem de nível de linha funciona para código gerenciado e nativo. Os relatórios de desempenho que exibem esses dados incluem a exibição de Linhas e a exibição de Módulos.

 Informações de início/término de caractere não estão disponíveis para código nativo. Para instruções de várias linhas, as informações de início da linha não estão disponível para código nativo. Somente informações de final da linha estão disponíveis.

### <a name="available-data"></a>Dados disponíveis
 Os dados de amostragem de nível de linha disponíveis incluem as seguintes informações:

- Nome da função.

- Endereço da função.

- Início da linha – número de linha do código do qual foi obtida a amostra.

- Fim da linha – número de linha de término do código-fonte. Esse geralmente é o mesmo que os dados do "Início da linha", exceto quando uma única instrução do programa abrange várias linhas do código-fonte.

- Início do caractere – coluna de início da amostra de agregação. É geralmente 0, exceto quando uma única linha contém várias instruções de programa.

- Final do caractere – coluna de término do exemplo de agregação.

- IP – endereço em que o exemplo de agregação foi obtido (somente em modo de exibição de IP).

  Na exibição de **Módulos**, se uma função tiver estatísticas em nível de linha, as estatísticas estarão aninhadas em cada função. Além disso, são apresentadas as estatísticas no nível de IP que estão aninhadas em cada linha.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Desligar a amostragem no nível de linha para o código gerenciado
 Por padrão, a amostragem de nível de linha está ativada. Desligue a coleta de dados no nível de linha para o código gerenciado usando um dos seguintes comandos:

- Antes da criação de perfil, digite **VSPerfCLREnv /samplelineoff**. Isso afeta os aplicativos e os serviços.

     — ou —

- Ao iniciar um aplicativo, digite **VSPerfCmd/LineOff \<other arguments>**.

## <a name="see-also"></a>Confira também
- [Configurar sessões de desempenho](../profiling/configuring-performance-sessions.md)
- [Analisar dados de ferramentas de desempenho](../profiling/analyzing-performance-tools-data.md)
