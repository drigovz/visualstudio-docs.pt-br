---
title: PerfTips | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09009e3815ee70b13f3397ab68fa9b0c4d767f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174610"
---
# <a name="perftips"></a>PerfTips
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O depurador do Visual Studio *PerfTips* e as **Ferramentas de Diagnóstico** integradas ao depurador ajudam a monitorar e analisar o desempenho de seu aplicativo durante a depuração.  
  
 Embora as ferramentas de diagnóstico integradas ao depurador sejam uma ótima maneira de descobrir problemas de desempenho durante o desenvolvimento, o depurador pode exercer um impacto significativo sobre o desempenho do seu aplicativo. Para coletar dados de desempenho mais precisos, considere usar também as ferramentas de diagnóstico do Visual Studio que são executados fora do depurador como uma parte adicional das suas investigações de desempenho. Ver [executar ferramentas de criação de perfil sem depuração](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
## <a name="perftips"></a>PerfTips  
 Quando o depurador interrompe a execução em um ponto de interrupção ou operação passo a passo, o tempo decorrido entre a interrupção e o ponto de interrupção anterior aparece como uma dica na janela do editor. Para obter mais informações, consulte [PerfTips: informações de desempenho imediatas durante a depuração com o Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx).  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Janela Ferramentas de Diagnóstico  
 Pontos de interrupção e dados de tempo associados são registrados na janela Ferramentas de Diagnóstico  
  
 O gráfico a seguir mostra a janela Ferramentas de Diagnóstico no Visual Studio 2015 Atualização 1:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   A linha do tempo **Eventos de Interrupção** marca os pontos de interrupção atingidos na sessão de depuração. Clique em um evento para selecioná-lo na lista de detalhes do **Depurador**.  
  
-   O gráfico **Utilização de CPU** mostra a alteração na utilização da CPU entre todos os núcleos de processador na sessão de depuração.  
  
-   A lista **Eventos** do painel de detalhes **Depurador** inclui itens para cada evento de interrupção.  
  
-   A coluna **Duração** de um evento de interrupção exibe o tempo decorrido entre o evento e o ponto de interrupção anterior.  
  
## <a name="turn-perftips-on-or-off"></a>Ativar ou desativar PerfTips  
 Para habilitar ou desabilitar PerfTips:  
  
1.  No menu **Depurar**, escolha **Opções**.  
  
2.  Marque ou desmarque **Mostrar tempo decorrido PerfTip durante a depuração**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Ativar ou desativar a janela de Ferramentas de Diagnóstico  
 Para habilitar ou desabilitar a janela de Ferramentas de Diagnóstico:  
  
1.  No menu **Depurar**, escolha **Opções**.  
  
2.  Marque ou desmarque **Habilitar ferramentas de diagnóstico durante a depuração**.



