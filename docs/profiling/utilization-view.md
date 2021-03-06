---
title: Exibição de Utilização | Microsoft Docs
description: Saiba que a exibição utilização exibe informações sobre a CPU, a GPU e outros recursos do sistema que são usados pelo processo atual.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 52dd5611e5a05de4bdb2d765bbdd2860e54f767e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885892"
---
# <a name="utilization-view"></a>Exibição Utilização
A **Exibição Utilização** exibe informações sobre a CPU, a GPU e outros recursos do sistema usados pelo processo atual (escolha **Analisar** > **Visualizador de Simultaneidade** para iniciar o visualizador de simultaneidade). Ela mostra a utilização média do núcleo pelo processo analisado, o processo ocioso, o processo do Sistema e outros processos em execução no sistema ao longo do tempo. Ela não mostra qual núcleo específico está ativo em um determinado momento. Por exemplo, se dois núcleos estiverem sendo executados individualmente com capacidade de 50% durante um período específico, essa exibição mostrará um núcleo lógico sendo utilizado. A exibição é gerada pela divisão do tempo de criação de perfil em segmentos de tempo curto. Para cada segmento, o grafo plota o número médio de threads de processos em execução nos núcleos lógicos durante esse intervalo.

 ![Exibição Utilização da CPU](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 O gráfico mostra o tempo (no eixo x) e os núcleos lógicos médios utilizados pelo processo de destino, o processo ocioso e o processo do Sistema. (O processo ocioso mostra núcleos ociosos. O processo do sistema é um processo no Windows que pode executar o trabalho em nome de outros processos.) Os processos restantes que estão sendo executados na conta do sistema para a utilização de qualquer núcleo restante.

 O número de núcleos lógicos é mostrado no eixo y. O Windows trata o suporte simultâneo de multithreading em hardware como núcleos lógicos (por exemplo, Hyper-Threading). Portanto, um sistema com um processador quad-core que oferece suporte a dois threads de hardware por núcleo é exibido como um sistema de oito núcleos lógicos. Isso também se aplica à exibição Núcleos. Para obter mais informações, consulte [exibição de núcleos](../profiling/cores-view.md).

 O gráfico de atividade da GPU mostra o número de mecanismos do DirectX em uso ao longo do tempo.  Um mecanismo está em uso se ele estiver processando um pacote DMA.  O gráfico não mostra o mecanismo de DirectX específico (por exemplo, mecanismo 3D, de vídeo e outros).

## <a name="purpose"></a>Finalidade
 Recomendamos a Exibição de Utilização como ponto de partida para investigações de desempenho quando você usar a Visualização Simultânea. Como ela fornece uma visão geral do grau de simultaneidade de um aplicativo ao longo do tempo, é possível usá-la para identificar rapidamente as áreas que precisam de ajuste de desempenho ou paralelização.

 Se estiver interessado no ajuste de desempenho, você poderá estar tentando identificar comportamentos que não atendem às suas expectativas. Você pode também estar procurando pela existência e causa das regiões com pouca utilização de núcleos lógicos de CPU. Também é possível que você esteja procurando padrões de uso entre a CPU e a GPU.

 Se você estiver interessado na paralelização de um aplicativo, provavelmente estará procurando áreas de execução vinculadas à CPU ou áreas em que você não está usando a CPU.

 Áreas vinculadas à CPU aparecem em verde. O gráfico mostrará um núcleo sendo usado se o aplicativo for serial.

 As áreas em que você não está usando a CPU aparecem em cinza. Tais áreas podem representar pontos em que o aplicativo fica ocioso ou executa um bloqueio E/S que proporciona oportunidades para paralelismo por meio da sobreposição com outro trabalho vinculado à CPU.

 Ao encontrar um comportamento de interesse, é possível ampliar a região por meio da seleção. Após a aplicação do zoom, é possível mudar para a Exibição de Threads ou a Exibição de Núcleos para obter uma análise mais detalhada.

 Se você estiver usando a GPU por meio do C++ AMP ou DirectX, poderá ser interessante identificar o número de mecanismos GPU em uso ou de áreas em que a GPU é inesperadamente ociosa.

## <a name="zoom"></a>Zoom
 Para ampliar o gráfico de Utilização de CPU ou de GPU, selecione uma seção ou use a ferramenta de controle deslizante de zoom acima do gráfico. A configuração de zoom persiste conforme você muda para outros modos. Para reduzir novamente, use a ferramenta de controle deslizante de zoom. Você também pode aplicar zoom usando **Ctrl** + **Scroll**.

## <a name="see-also"></a>Confira também
- [Visualizador de Simultaneidade](../profiling/concurrency-visualizer.md)
- [Exibição de núcleos](../profiling/cores-view.md)