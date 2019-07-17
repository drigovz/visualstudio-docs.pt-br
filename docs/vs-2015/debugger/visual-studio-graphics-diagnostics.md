---
title: Diagnóstico de gráficos do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb55508c705013c3ad604c3ceeb52d7af6bb4445
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158456"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio*diagnóstico de gráficos* é um conjunto de ferramentas de registro e, em seguida, analisando problemas de desempenho e a renderização em aplicativos Direct3D. Diagnóstico de gráficos pode ser usado em aplicativos que estão sendo executadas localmente no seu PC com Windows, em um emulador de dispositivo do Windows ou em um dispositivo ou computador remoto.  
  
 O fluxo de trabalho de diagnóstico de gráficos começa com a captura de um registro de como seu aplicativo usa o Direct3D — ao vivo, enquanto ele é executado — para que seu comportamento pode ser analisado imediatamente, compartilhados ou salvas para uso posterior. Sessões de captura podem ser iniciadas e controladas manualmente do Visual Studio ou com a ferramenta de linha de comando de captura **dxcap.exe**. Sessões de captura também podem ser iniciadas e controladas programaticamente usando as APIs de captura do diagnóstico de gráficos.  
  
 Depois que uma sessão de captura foi registrada seu conteúdo pode ser reproduzido pelo Visual Studio *analisador de gráficos* a qualquer momento, recriando os quadros capturados usando os mesmos recursos exatos e o aplicativo usado comandos de renderização. Em seguida, usando as ferramentas fornecidas na janela do analisador de gráficos, qualquer um dos quadros capturados podem ser analisados em detalhes. Essas ferramentas podem ser usadas para examinar qualquer chamada à API do Direct3D, recursos, o objeto de estado do pipeline, estágio de pipeline ou até mesmo o histórico completo de qualquer pixel em um quadro capturado. Usando essas ferramentas em conjunto, um problema de renderização pode ser explorado intuitivamente, começando em como ela aparece em um quadro capturado e aprofundar-se a causa raiz em ativos de código, sombreadores ou elementos gráficos de código-fonte do aplicativo.  
  
 Para diagnosticar problemas de desempenho, um quadro capturado pode ser analisado usando as *análise de quadros* ferramenta. Essa ferramenta explora as otimizações de desempenho potencial automaticamente alterando o modo como o aplicativo usa o Direct3D e benchmark todas as variações para você. No passado, você pode ter feito e por benchmark esses tipos de alterações manualmente apenas para localizar quais fizeram uma diferença de fora. Com análise de quadro, você só precisará fazer as alterações que você já conhece valerá a.  
  
 Diagnóstico de gráficos ajuda seu aplicativo do Direct3D graficamente ricos examinar e executar o melhor desempenho.  
  
 Continuar a [visão geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md) para saber mais sobre o que oferece diagnóstico de gráficos do Visual Studio.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Apresenta o fluxo de trabalho e as ferramentas de Diagnóstico de Gráficos.  
  
 [Introdução](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Nesta seção, você aprenderá como instalar o diagnóstico de gráficos do Visual Studio e como começar a usar o diagnóstico de gráficos com seu aplicativo Direct3D.  
  
 [Capturando informações de gráficos](../debugger/capturing-graphics-information.md)  
 Para usar o Diagnóstico de Gráficos para examinar um problema de renderização no aplicativo, primeiro registre informações sobre como o aplicativo usa o DirectX. Durante a sessão de gravação, enquanto o aplicativo é executado normalmente, você *captura* (ou seja, seleciona) os quadros de interesse. A captura contém informações detalhadas sobre como os quadros são renderizados. É possível salvar as informações capturadas como um documento de log de gráficos para examinar mais tarde ou compartilhar com outros membros da equipe.  
  
 [Uso de GPU](../debugger/gpu-usage.md)  
 Para usar o diagnóstico de gráficos para analisar seu aplicativo, use a ferramenta de uso de GPU. Uso de GPU pode ser usado em conjunto com outras ferramentas de criação de perfil, como o uso da CPU, para correlacionar a atividade de CPU e GPU que pode causar problemas de desempenho em seu aplicativo.  
  
 [Documento de log de gráficos](../debugger/graphics-log-document.md)  
 Para começar o exame de um log de gráficos registrado, use a janela do documento de Log de Gráficos para selecionar um quadro capturado (ou mesmo um pixel específico) para que seja possível examinar em detalhes os *eventos* (ou seja, as chamadas à API DirectX) que o afetam.  
  
 [Análise de quadros](../debugger/graphics-frame-analysis.md)  
 Depois de selecionar um quadro, use a Análise de Quadros de Gráficos para examinar e ajustar seu desempenho de renderização.  
  
 [Lista de Eventos](../debugger/graphics-event-list.md)  
 Depois de selecionar um quadro, use a **Lista de Eventos de Gráficos** para examinar os eventos e determinar se eles estão relacionados ao problema de renderização.  
  
 [Estado](../debugger/graphics-state.md)  
 A janela de estado ajuda a entender o estado dos gráficos que está ativo no momento do evento atual.  
  
 [Estágios de Pipeline](../debugger/graphics-pipeline-stages.md)  
 Na janela **Estágios do Pipeline de Gráficos**, investigue como o evento selecionado no momento é processado pelos estágios do pipeline gráfico para que seja possível identificar onde o problema de renderização aparece pela primeira vez. Examinar os estágios do pipeline é especialmente útil quando um objeto não aparece devido a uma transformação incorreta ou quando um dos estágios produz uma saída que não corresponde ao que o próximo estágio espera.  
  
 [Pilha de Chamadas do Evento](../debugger/graphics-event-call-stack.md)  
 Use a **Pilha de Chamadas do Evento de Gráficos** para examinar a pilha de chamadas do evento selecionado no momento para que seja possível navegar até o código de aplicativo relacionado ao problema de renderização.  
  
 [Histórico de Pixel](../debugger/graphics-pixel-history.md)  
 Usando a janela **Histórico de Pixel de Gráficos** para analisar como o pixel selecionado no momento é afetado pelos eventos que o influenciaram, é possível identificar o evento ou a combinação de eventos que causam certos tipos de problemas de renderização. O histórico de pixel é especialmente útil quando um objeto é renderizado incorretamente porque a saída do sombreador de pixel está incorreta ou foi combinada incorretamente com o buffer de quadro, ou quando um objeto não aparece porque seus pixels foram descartados antes de atingir o buffer de quadro.  
  
 [Tabela de Objeto](../debugger/graphics-object-table.md)  
 Use a **Tabela de Objetos Gráficos** para examinar as propriedades e o conteúdo de objetos e recursos do Direct3D específicos em vigor para o evento selecionado no momento. A tabela de objetos pode ajudar a determinar o contexto do dispositivo gráfico que está ativo durante um evento e examinar os conteúdos de recursos gráficos, como buffers constantes, buffers de vértices e texturas.  
  
 [Depurador HLSL](../debugger/hlsl-shader-debugger.md)  
 Para examinar como o código do sombreador para o evento selecionado no momento e o estágio do pipeline de gráficos se comportam, use o **Depurador HLSL** para percorrer o código, examinar o conteúdo das variáveis e realizar outras tarefas típicas de depuração. Também é possível usar o depurador HLSL para examinar o código do sombreador de computação, independente de os resultados serem processados mais pelo pipeline de gráficos ou apenas relidos pelo aplicativo.  
  
 [Ferramenta de captura de linha de comando](../debugger/command-line-capture-tool.md)  
 Use a ferramenta de captura de linha de comando para capturar e reproduzir rapidamente informações de gráficos sem usar o Visual Studio ou captura programática. Em particular, você pode usar a ferramenta de captura de linha de comando para automação ou em um ambiente de teste.  
  
 [Exemplos](../debugger/graphics-diagnostics-examples.md)  
 Vários exemplos demonstram como usar as ferramentas de Diagnóstico de Gráficos juntas para diagnosticar diferentes tipos de problemas de renderização.  
  
## <a name="related-sections"></a>Seções relacionadas  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)|Apresenta a funcionalidade de depuração no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Gráficos e jogos DirectX](http://go.microsoft.com/fwlink/?LinkId=256498)|Fornece artigos que discutem as tecnologias de gráficos do DirectX.|
