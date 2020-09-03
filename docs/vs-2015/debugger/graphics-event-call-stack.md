---
title: Pilha de chamadas de evento de gráficos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8344050d26286263e0c33974b976e4ae25ff18de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192749"
---
# <a name="graphics-event-call-stack"></a>Pilha de chamadas de gráfico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A pilha de chamadas de evento de gráficos no Analisador de Gráficos do Visual Studio ajuda a mapear a relação entre eventos gráficos problemáticos e o código-fonte do seu aplicativo.  
  
 Esta é a janela de pilha de chamadas de evento:  
  
 ![A pilha de chamadas que precede um evento DrawIndexed.](../debugger/media/gfx-diag-demo-graphics-event-call-stack-orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Noções básicas sobre a pilha de chamadas do evento de gráficos  
 Você pode usar a pilha de chamadas de evento para entender o fluxo de execução que levou a um evento Direct3D específico. Ele é semelhante à janela de pilha de chamadas do Visual Studio, exceto que, em vez de exibir a pilha de chamadas atual do thread ativo em um aplicativo em execução, ele exibe a pilha de chamadas como existia quando o evento de Direct3D selecionado ocorreu. Na pilha de chamadas de evento, você pode ir para o local de chamada do evento Direct3D selecionado para inspecionar o código ao redor.  
  
 Usando a Pilha de Chamadas do Evento para identificar o caminho do código de origem de um evento de problema, você pode usar o seu conhecimento sobre o código na base para deduzir possíveis origens do problema ou você pode adicionar pontos de interrupção no código-fonte do aplicativo para usar técnicas de depuração tradicionais e examinar como o estado do aplicativo ou parâmetros do evento estão fazendo com que o evento se comporte incorretamente. Esse exame pode ajudá-lo a encontrar problemas no código-fonte que são manifestados somente como problemas de renderização.  
  
### <a name="graphics-event-call-stack-information"></a>Informações sobre a pilha de chamadas de gráfico  
 A pilha de chamadas de evento não dá suporte a eventos de pré-quadro ou a eventos definidos pelo usuário. A pilha de chamadas de eventos de gráficos é exibida em um formato de tabela.  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Nome**|Um símbolo que identifica a função que contém o site de chamada. O símbolo de depuração da função é exibido quando ela está disponível. Caso contrário, o deslocamento de função é exibido.|  
|**Arquivo**|O nome do arquivo do código-fonte ou arquivo de biblioteca que contém o site de chamada.|  
|**Localidade**|O número de linha do site de chamada.|  
  
### <a name="links-to-graphics-objects"></a>Links a objetos de gráficos  
 Para entender o evento de gráficos selecionado, talvez seja necessário obter informações sobre os objetos do Direct3D associados a ele. A janela **pilha de chamadas de evento de gráficos** fornece links para essas informações.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: Objetos ausentes devido ao sombreamento de vértice](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)
