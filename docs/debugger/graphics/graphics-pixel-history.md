---
title: Histórico de pixels de gráficos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cb1b7a869915eebc561e1baf47082dd5dbc00df
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735480"
---
# <a name="graphics-pixel-history"></a>Histórico de pixel gráfico
A janela Histórico de pixels de gráficos no Analisador de Gráficos do Visual Studio ajuda a entender como um pixel específico é afetado pelos eventos do Direct3D que ocorrem durante um quadro de seu jogo ou aplicativo.

 Esta é a janela de histórico de pixel:

 ![Um pixel com três eventos do Direct3D em seu histórico.](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")

## <a name="understanding-the-pixel-history-window"></a>Compreendendo a janela de histórico de pixels
 Usando o histórico de pixel, você pode analisar como um pixel específico do destino de renderização é afetado pelos eventos do Direct3D durante um quadro. Você pode identificar um problema de processamento de um evento específico do Direct3D, mesmo quando eventos subsequentes — ou primitivas subsequentes no mesmo evento — continuam a alterar o valor de cor final do pixel. Por exemplo, um pixel pode ser processado incorretamente e obscurecido por outro pixel semitransparente, para que as cores sejam combinadas no framebuffer. Esse tipo de problema seria difícil de diagnosticar se você tivesse apenas o conteúdo final do destino da renderização para orientá-lo.

 A janela de histórico de pixel exibe o histórico completo de um pixel durante o curso do quadro selecionado. O **Buffer de Quadro Final** na parte superior da janela exibe a cor escrita no framebuffer no final do quadro, além de informações adicionais sobre o pixel, como o seu quadro de origem e coordenada da tela. Essa área também contém a caixa de seleção **Renderizar Alfa**. Quando a caixa de seleção estiver marcada, a cor do **Buffer de Quadro Final** e os valores de cor intermediários são exibidos com transparência sobre um padrão quadriculado. Se a caixa de seleção estiver desmarcada, o canal alfa dos valores de cor será ignorado.

 A parte inferior da janela exibe os eventos que podem afetar a cor do pixel, com os pseudoeventos **Inicial** e **Final** que representam os valores de cor inicial e final do pixel no framebuffer. O valor de cor inicial é determinado pelo primeiro evento que alterou a cor do pixel (geralmente um evento `Clear`). Um pixel sempre tem esses dois pseudo-eventos no seu histórico, mesmo quando outros eventos não o afetaram. Quando outros eventos podem afetar o pixel, eles são exibidos entre os eventos **Inicial** e **Final**. Os eventos podem ser expandidos para mostrar seus detalhes. No caso de eventos simples, como aqueles que limpam um destino de renderização, o efeito do evento é um valor de cor. Eventos mais complexos, como chamadas de desenho geram uma ou mais primitivas que podem colaborar com a cor do pixel.

 As primitivas que foram desenhadas pelo evento são identificadas por seu tipo e índice de primitiva, com a contagem total de primitiva do objeto. Por exemplo, um identificador como **Triângulo (1456) de (6214)** significa que a primitiva corresponde ao triângulo 1456º em um objeto que é composto de 6214 triângulos. À esquerda de cada identificador de primitiva há um ícone que resume o efeito que a primitiva tinha sobre o pixel. As primitivas que afetam a cor do pixel são representadas por um retângulo arredondado preenchido com a cor resultante. As primitivas que são excluídas devido a algum impacto sobre a cor do pixel são representadas por ícones que indicam o motivo pelo qual o pixel foi excluído. Esses ícones são descritos na seção [exclusão primitiva](#exclusion) mais adiante neste artigo.

 É possível expandir cada primitiva para examinar como a saída do sombreador do pixel foi mesclada com a cor do pixel existente para produzir a cor resultante. A partir disso você também pode examinar ou depurar o código de sombreador de pixel que está associado à primitiva e ampliar o nó do sombreador de vértice para examinar a entrada do sombreador de vértice.

### <a name="exclusion"></a> Exclusão de primitiva
 Quando uma primitiva é excluída por afetar a cor do pixel, a exclusão pode ocorrer por diversos motivos. Cada motivo é representado por um ícone que é descrito nesta tabela:

|Ícone|Motivo da exclusão|
|----------|--------------------------|
|![Ícone de falha de teste de profundidade.](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|O pixel foi excluído porque não passou no teste de profundidade.|
|![Ícone de falha de teste de tesoura.](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|O pixel foi excluído porque não passou no teste de tesoura.|
|![Ícone de falha de teste de estêncil.](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|O pixel foi excluído porque não passou no teste de estêncil.|

### <a name="draw-call-exclusion"></a>Exclusão de chamada de desenho
 Se todos as primitivas em uma chamada de desenho são excluídas por afetarem o destino de renderização porque não passaram em um teste, a chamada de desenho não pode ser expandida e um ícone que corresponde ao motivo da exclusão é exibido ao lado dela. Os motivos de exclusão da chamada de desenho se assemelha aos motivos de exclusão da primitiva e os ícones são semelhantes.

### <a name="viewing-and-debugging-shader-code"></a>Exibição e depuração do código do sombreador
 Você pode examinar e depurar o código para os sombreadores de vértice, envoltória, domínio, geometria e pixel usando os controles abaixo do primitivo associado ao sombreador.

##### <a name="to-view-a-shaders-source-code"></a>Para exibir o código-fonte do sombreador

1. Na janela **histórico de pixels de gráficos** , localize a chamada de desenho que corresponde ao sombreador que você deseja examinar e expanda-a.

2. Na chamada de desenho que você acabou de expandir, selecione um primitivo que demonstre o problema em que você está interessado e expanda-o.

3. Na primitiva em que você está interessado, siga o link do título do sombreador – por exemplo, siga o link **vértice do sombreador obj: 30** para exibir o código-fonte do sombreador de vértice.

    > [!TIP]
    > O número do objeto, **obj: 30**, identifica esse sombreador em toda a interface do analisador de gráficos, como na janela objetos de tabela e estágios de pipeline.

##### <a name="to-debug-a-shader"></a>Para depurar um sombreador

1. Na janela **histórico de pixels de gráficos** , localize a chamada de desenho que corresponde ao sombreador que você deseja examinar e expanda-a.

2. Em seguida, na chamada de desenho que você acabou de expandir, selecione um primitivo que demonstre o problema em que você está interessado e expanda-o.

3. Na primitiva em que você está interessado, escolha **Iniciar Depuração**. Esse ponto de entrada no depurador HLSL usa como padrão a primeira invocação do sombreador para o primitivo correspondente, ou seja, o primeiro pixel ou vértice processado pelo sombreador. Há apenas um pixel associado à primitiva, mas há mais de uma invocação de sombreador de vértice para linhas e triângulos.

     Para depurar a invocação do sombreador de vértice para um vértice específico, expanda o link de título VertexShader e localize o vértice no qual você está interessado e escolha **Iniciar Depuração** ao lado dele.

### <a name="links-to-graphics-objects"></a>Links a objetos de gráficos
 Para entender os eventos de gráficos no histórico de pixel, talvez você precise obter informações sobre o estado do dispositivo no momento do evento ou sobre os objetos do Direct3D referenciados pelo evento. Para cada evento no histórico de pixel, o **Histórico de Pixel de Gráficos** fornece links para o estado do dispositivo atual e para objetos relacionados.

## <a name="see-also"></a>Consulte também
- [Passo a passo: objetos ausentes devido ao estado do dispositivo](walkthrough-missing-objects-due-to-device-state.md)
- [Passo a passo: depurando erros de renderização devido ao sombreamento](walkthrough-debugging-rendering-errors-due-to-shading.md)