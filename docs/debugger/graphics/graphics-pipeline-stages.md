---
title: Estágios de pipeline de gráficos | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d697313289bbf00234764cc04603b7bc256f174
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735476"
---
# <a name="graphics-pipeline-stages"></a>Estágios de Pipeline Gráficos
A janela estágios de pipeline de gráficos ajuda você a entender como uma chamada de desenho individual é transformada por cada estágio do pipeline de gráficos do Direct3D.

 Esta é a janela estágios de pipeline:

 ![Um objeto 3D passa pelos estágios de pipeline.](media/gfx_diag_demo_pipeline_stages_orientation.png)

## <a name="understanding-the-graphics-pipeline-stages-window"></a>Noções básicas sobre a janela Estágios de Pipeline Gráficos
 A janela estágios de pipeline visualiza o resultado de cada estágio do pipeline gráfico separadamente, para cada chamada de desenho. Normalmente, os resultados de estágios no meio do pipeline estão ocultos, dificultando a localização de um problema de processamento iniciado. Ao visualizar cada estágio separadamente, a janela estágios de pipeline facilita a visualização de onde o problema começa — por exemplo, você pode ver facilmente quando o estágio do sombreador de vértice causa inesperadamente que um objeto seja desenhado fora da tela.

 Depois de identificar o estágio em que o problema ocorre, você pode usar as outras ferramentas do analisador de gráficos para examinar como os dados foram interpretados ou transformados. Os problemas de renderização que aparecem nos estágios de pipeline geralmente estão relacionados a descritores incorretos de formato de vértice, programas de sombreador de bugs ou estado configurado incorretamente.

### <a name="links-to-related-graphics-objects"></a>Links para objetos gráficos relacionados
 Às vezes, é necessário contexto adicional para determinar por que uma chamada de desenho interage de forma específica com o pipeline de gráficos. Para tornar esse contexto adicional mais fácil de localizar, o pipeline de gráficos estágios da janela leva a um ou mais objetos que fornecem contexto adicional relacionado ao que está acontecendo no pipeline de gráficos.

- No Direct3D 12, esse objeto é geralmente uma lista de comandos.

- No Direct3D 11, esse objeto é geralmente um contexto de dispositivo de gráficos.

  Esses links fazem parte da assinatura de evento de gráficos atual localizada no canto superior esquerdo da janela de estágios de pipeline de gráficos. Siga qualquer um desses links para examinar detalhes adicionais sobre o objeto.

### <a name="viewing-and-debugging-shader-code"></a>Exibição e depuração do código do sombreador
 Você pode examinar e depurar o código para os sombreadores de vértice, envoltória, domínio, geometria e pixel usando os controles na parte inferior de seus respectivos estágios na janela estágios de pipeline.

#### <a name="to-view-a-shaders-source-code"></a>Para exibir o código-fonte do sombreador

- Na janela **estágios de pipeline de gráficos** , localize o estágio do sombreador que corresponde ao sombreador que você deseja examinar. Em seguida, abaixo da imagem de visualização, siga o link de título de estágio do sombreador – por exemplo, siga o link **vértice do sombreador obj: 30** para exibir o código-fonte do sombreador do vértice.

    > [!TIP]
    > O número do objeto, **obj: 30**, identifica esse sombreador em toda a interface do analisador de gráficos, como na janela de objeto e no histórico de pixels.

#### <a name="to-debug-a-shader"></a>Para depurar um sombreador

- Na janela **estágios de pipeline de gráficos** , localize o estágio do sombreador que corresponde ao sombreador que você deseja depurar. Em seguida, abaixo da imagem de visualização, escolha **Iniciar Depuração**. Esse ponto de entrada no depurador HLSL usa como padrão a primeira invocação do sombreador para o estágio correspondente, ou seja, o primeiro pixel, vértice ou primitiva que é processado pelo sombreador durante essa chamada de desenho. As invocações deste sombreador para um pixel ou vértice específico podem ser acessadas por meio do **histórico de pixels de gráficos**.

### <a name="the-pipeline-stages"></a>Os estágios de pipeline
 A janela estágios de pipeline visualiza apenas os estágios do pipeline que estavam ativos durante a chamada de desenho. Cada estágio do pipeline gráfico transforma a entrada do estágio anterior e passa o resultado para o próximo estágio. O primeiro estágio — o Assembler de entrada — usa dados de índice e vértice do seu aplicativo como sua entrada; o último estágio — a mesclagem de saída — combina pixels recém renderizados junto com o conteúdo atual do framebuffer ou destino de renderização como sua saída para produzir a imagem final que você vê na tela.

> [!NOTE]
> Os sombreadores de computação não têm suporte na janela **Estágios de Pipeline Gráficos**.

 **Montador de entrada** O Assembler de entrada lê os dados de índice e vértice especificados pelo seu aplicativo e o monta para o hardware de gráficos.

 Na janela estágios de pipeline, a saída do montador de entrada é visualizada como um modelo de wireframe. Para obter uma análise mais detalhada do resultado, selecione **Assembler de entrada** na janela **estágios de pipeline de gráficos** para exibir os vértices montados em 3D completo usando o editor de modelo.

> [!NOTE]
> Se a semântica `POSITION` não estiver presente na saída do assembler de entrada, nada é exibido no estágio **Entrada do Assembler**.

 **Sombreador de vértice** O estágio do sombreador de vértice processa vértices, normalmente executando operações como transformação, aparência e iluminação. Os sombreadores de vértice produzem o mesmo número de vértices que eles adotam como entrada.

 Na janela estágios de pipeline, a saída do sombreador de vértice é visualizada como uma imagem rasterizada de wireframe. Para obter uma análise mais detalhada do resultado, selecione o **sombreador de vértice** no **pipeline de gráficos estágios** janelas para exibir os vértices processados no editor de imagens.

> [!NOTE]
> Se a semântica `POSITION` ou `SV_POSITION` não estiver presente na saída do sombreador de vértice, nada é exibido no estágio **Sombreador de Vértice**.

 **Sombreador envoltória** (somente Direct3D 11 e Direct3D 12) o estágio do sombreador envoltória processa pontos de controle que definem uma superfície de ordem inferior, como uma linha, um triângulo ou um quatro. Como saída, ele produz um patch de geometria de ordem superior e constantes de patch que são transmitidas para o estágio de mosaico de função fixa.

 O estágio do sombreador envoltória não é visualizado na janela estágios de pipeline.

 **Estágio Tessellator** (somente Direct3D 11 e Direct3D 12) o estágio Tessellator é uma unidade de hardware de função fixa (não programável) que processa o domínio representado pela saída do sombreador envoltória. Como saída, ele cria um padrão de amostragem do domínio e um conjunto de primitivos menores — pontos, linhas, triângulos — que conectam esses exemplos.

 O estágio Tessellator não é visualizado na janela estágios de pipeline.

 **Sombreador de domínio** (somente Direct3D 11 e Direct3D 12) o estágio de sombreador de domínio processa patches de geometria de ordem superior do sombreador envoltória, juntos fatores de mosaico do estágio de mosaico. Os fatores de mosaico podem incluir fatores de entrada Tessellator, bem como fatores de saída. Como saída, ele calcula a posição de vértice de um ponto no patch de saída de acordo com os fatores de Tessellator.

 O estágio do sombreador de domínio não é visualizado na janela estágios de pipeline.

 **Sombreador de geometria** O estágio Geometry Shader processa primitivos inteiros, pontos, linhas ou triângulos, juntamente com dados de vértice opcionais para primitivos adjacentes de borda. Ao contrário dos sombreadores de vértice, os sombreadores de geometria podem produzir mais ou menos primitivos do que eles utilizam como entrada.

 Na janela estágios de pipeline, a saída do sombreador de geometria é visualizada como uma imagem rasterizada de wireframe. Para obter uma análise mais detalhada do resultado, selecione **sombreador de geometria** na janela **estágios de pipeline de gráficos** para exibir os primitivos processados no editor de imagens.

 **Estágio de saída do fluxo** O estágio de saída de fluxo pode interceptar primitivos transformados antes da rasterização e gravá-los na memória; a partir daí, os dados podem ser recirculados como entrada para os estágios anteriores do pipeline de gráficos ou ser lidos de volta pela CPU.

 O estágio de saída do fluxo não é visualizado na janela estágios de pipeline.

 **Estágio do rasterizador** O estágio rasterizador é uma unidade de hardware de função fixa (não programável) que converte primitivos de vetor – pontos, linhas, triângulos — em uma imagem rasterizada executando a conversão de linha de verificação. Durante os vértices de rasterização são transformados no clipe homogêneo e recortados. Como saída, os sombreadores de pixel são mapeados e os atributos por vértice são interpolados na primitiva e ficam prontos para o sombreador de pixel.

 O estágio rasterizador não é visualizado na janela estágios de pipeline.

 **Sombreador de pixel** O estágio de sombreador de pixel processa primitivos rasterizados junto com dados de vértice interpolados para gerar valores por pixel, como cor e profundidade.

 Na janela estágios de pipeline, a saída do sombreador de pixel é visualizada como uma imagem rasterizada de cor completa. Para ver mais de perto o resultado, selecione **sombreador de pixel** na janela **estágios de pipeline de gráficos** para exibir os primitivos processados no editor de imagens.

 **Fusão de saída** O estágio de fusão de saída combina o efeito de pixels recém renderizados junto com o conteúdo existente de seus buffers correspondentes — Color, Depth e stencil — para produzir novos valores nesses buffers.

 Na janela estágios de pipeline, a saída da mesclagem de saída é visualizada como uma imagem rasterizada de cor completa. Para examinar os resultados mais detalhadamente, selecione **fusão de saída** na janela estágios de **pipeline de gráficos** para exibir o framebuffer mesclado.

### <a name="vertex-and-geometry-shader-preview"></a>Visualização de vértice e do sombreador de geometria
 Quando você seleciona o ponto de vértice ou o estágio do sombreador de geometria na janela **estágios de pipeline** , você pode exibir as entradas e saídas do sombreador no painel abaixo.  Aqui, você encontrará detalhes sobre a lista de vértices fornecidos aos sombreadores depois que eles tiverem sido montados pelo estágio de Assembler de entrada.

 ![Visualizador do buffer de entrada do estágio do sombreador de vértice](media/gfx_diag_vertex_shader_inbuffers.png)

 Para exibir o resultado do estágio do sombreador de vértice, escolha a miniatura do estágio do sombreador de vértice para exibir um wireframe de tamanho completo e rasterizado da malha após sua transformação pelo sombreador de vértice.

 ![A visualização do resultado do estágio do sombreador de vértice](media/gfx_diag_vertex_shader_preview.png)

## <a name="see-also"></a>Consulte também
- [Passo a passo: objetos ausentes devido ao sombreamento de vértice](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Passo a passo: depurando erros de renderização devido ao sombreamento](walkthrough-debugging-rendering-errors-due-to-shading.md)