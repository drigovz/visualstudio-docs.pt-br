---
title: Diagnóstico de Gráficos do Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 29ca6b2110038a427c76622d50f769321cda9ff9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296913"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio*diagnóstico de gráficos* é um conjunto de ferramentas para gravar e analisar problemas de desempenho e renderização em aplicativos Direct3D. Diagnóstico de Gráficos pode ser usado em aplicativos que estão sendo executados localmente em seu computador Windows, em um emulador de dispositivo do Windows ou em um computador ou dispositivo remoto.  
  
 O fluxo de trabalho de Diagnóstico de Gráficos começa capturando um registro de como seu aplicativo usa o Direct3D — ao vivo, à medida que é executado — para que seu comportamento possa ser analisado imediatamente, compartilhado ou salvo para mais tarde. As sessões de captura podem ser iniciadas e controladas manualmente no Visual Studio ou com a ferramenta de captura de linha de comando **dxcap. exe**. As sessões de captura também podem ser iniciadas e controladas programaticamente usando as APIs de captura Diagnóstico de Gráficos.  
  
 Depois que uma sessão de captura tiver sido registrada, seu conteúdo poderá ser reproduzido pelo *analisador de gráficos* do Visual Studio a qualquer momento, recriando os quadros capturados usando exatamente os mesmos recursos e processando comandos usados pelo aplicativo. Em seguida, usando as ferramentas fornecidas na janela analisador de gráficos, qualquer um dos quadros capturados pode ser analisado em detalhes. Essas ferramentas podem ser usadas para examinar qualquer chamada à API do Direct3D, recurso, objeto de estado do pipeline, estágio do pipeline ou até mesmo o histórico completo de qualquer pixel em um quadro capturado. Ao usar essas ferramentas em conjunto, um problema de renderização pode ser explorado intuitivamente, começando de como ele aparece em um quadro capturado e fazendo uma busca detalhada em sua causa raiz no código-fonte, nos sombreadores ou nos ativos gráficos do aplicativo.  
  
 Para diagnosticar problemas de desempenho, um quadro capturado pode ser analisado usando a ferramenta de *análise de quadros* . Essa ferramenta explora otimizações de desempenho potenciais alterando automaticamente a maneira como o aplicativo usa Direct3D e benchmarking de todas as variações para você. No passado, você pode ter feito e fazer o benchmark desses tipos de alterações manualmente apenas para descobrir quais fizeram uma diferença. Com a análise de quadros, você só precisa fazer as alterações que já conhecem serão pagas.  
  
 Diagnóstico de Gráficos ajuda sua aparência do aplicativo Direct3D graficamente rica e a melhor execução.  
  
 Continue na [visão geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md) para saber mais sobre o que o Visual Studio diagnóstico de gráficos oferece.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Apresenta o fluxo de trabalho e as ferramentas de Diagnóstico de Gráficos.  
  
 [Introdução](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Nesta seção, você aprenderá como instalar o Visual Studio Diagnóstico de Gráficos e como começar a usar o Diagnóstico de Gráficos com seu aplicativo do Direct3D.  
  
 [Capturando informações de gráficos](../debugger/capturing-graphics-information.md)  
 Para usar o Diagnóstico de Gráficos para examinar um problema de renderização no aplicativo, primeiro registre informações sobre como o aplicativo usa o DirectX. Durante a sessão de gravação, enquanto o aplicativo é executado normalmente, você *captura* (ou seja, seleciona) os quadros de interesse. A captura contém informações detalhadas sobre como os quadros são renderizados. É possível salvar as informações capturadas como um documento de log de gráficos para examinar mais tarde ou compartilhar com outros membros da equipe.  
  
 [Uso de GPU](../debugger/gpu-usage.md)  
 Para usar Diagnóstico de Gráficos para criar o perfil de seu aplicativo, use a ferramenta uso de GPU. O uso de GPU pode ser usado em conjunto com outras ferramentas de criação de perfil, como o uso da CPU, para correlacionar a atividade de CPU e GPU que podem contribuir para problemas de desempenho em seu aplicativo.  
  
 [Documento de log de gráficos](../debugger/graphics-log-document.md)  
 Para começar o exame de um log de gráficos registrado, use a janela do documento de Log de Gráficos para selecionar um quadro capturado (ou mesmo um pixel específico) para que seja possível examinar em detalhes os *eventos* (ou seja, as chamadas à API DirectX) que o afetam.  
  
 [Análise de quadros](../debugger/graphics-frame-analysis.md)  
 Depois de selecionar um quadro, use a Análise de Quadros de Gráficos para examinar e ajustar seu desempenho de renderização.  
  
 [Lista de Eventos](../debugger/graphics-event-list.md)  
 Depois de selecionar um quadro, use a **Lista de Eventos de Gráficos** para examinar os eventos e determinar se eles estão relacionados ao problema de renderização.  
  
 [Estado](../debugger/graphics-state.md)  
 A janela estado ajuda você a entender o estado de gráficos que está ativo no momento do evento atual.  
  
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
  
## <a name="related-sections"></a>Seções Relacionadas  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)|Apresenta a funcionalidade de depuração no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Gráficos e jogos do DirectX](https://go.microsoft.com/fwlink/?LinkId=256498)|Fornece artigos que discutem as tecnologias de gráficos do DirectX.|
