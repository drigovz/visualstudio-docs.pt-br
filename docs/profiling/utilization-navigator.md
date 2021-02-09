---
title: Navegador da Utilização | Microsoft Docs
description: Saiba como você pode usar o navegador de utilização no Visualizador de simultaneidade para selecionar um intervalo de tempo em um rastreamento.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d92747bb90cae18a79e81e49689ce8c01b8a9b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917573"
---
# <a name="utilization-navigator"></a>Navegador da utilização
É possível usar o Navegador da Utilização na Visualização Simultânea para selecionar um intervalo de tempo em um rastreamento. A Visualização Simultânea mostra o uso dos núcleos da CPU pelo processe de destino ao longo do tempo. Assim, fica mais fácil examinar os padrões de uso da CPU e comparar os dados de uso e dados de outras exibições. O Navegador da Utilização aparece na parte superior de cada exibição da Visualização Simultânea. A ilustração a seguir mostra o Navegador da Utilização.

 ![Navegador de utilização mostrando o período de tempo selecionado](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") Navegador de utilização e um intervalo de tempo selecionado

 Na ilustração, o intervalo selecionado é definido por um retângulo vermelho, conhecido como *elevador*.

 Veja como usar o Navegador da Utilização para manipular o intervalo de tempo exibido:

- É possível ter uma vista panorâmica ao arrastar o controle de posição para a esquerda ou direita. (Teclado: mova o foco para o elevador e, em seguida, pressione a tecla de direção para a esquerda ou direita.)

- É possível alterar a extensão do intervalo arrastando um dos identificadores. (Teclado: mova o foco para um identificador e, em seguida, pressione a tecla de direção para a direita ou esquerda.)

  Se o intervalo for alterado por meio de um controle de zoom diferente da Visualização Simultânea, o Navegador da Utilização se atualizará para refletir a mudança.