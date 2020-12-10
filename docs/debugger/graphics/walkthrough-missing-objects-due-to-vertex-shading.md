---
title: 'Walkthrough: objetos ausentes devido a sombreamento de vértice | Microsoft Docs'
description: Siga uma investigação que localize um erro de sombreador de vértice. Ele mostra a lista de eventos de elementos gráficos, estágios de pipeline de gráficos, depurador de HLSL e pilha de chamadas de eventos gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7e4c01a990ce4d3fff6769ba016c168b190687f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994989"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Passo a passo: Objetos ausentes devido ao sombreamento de vértice
Este tutorial demonstra como usar as [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para investigar um objeto ausente devido a um erro que ocorre durante o estágio do sombreador de vértice.

 Este tutorial ilustra essas tarefas:

- Usando a **lista de eventos gráficos** para localizar possíveis fontes do problema.

- Usando a janela **estágios de pipeline de gráficos** para verificar o efeito das chamadas à API do `DrawIndexed` Direct3D.

- Usando o **depurador HLSL** para examinar o sombreador de vértice.

- Usando a **pilha de chamadas de evento de gráficos** para ajudar a localizar a origem de uma constante HLSL incorreta.

## <a name="scenario"></a>Cenário
 Uma das causas comuns de um objeto ausente em um aplicativo 3D ocorre quando o sombreador de vértice transforma os vértices do objeto de maneira incorreta ou inesperada — por exemplo, o objeto pode ser dimensionado para um tamanho muito pequeno ou transformado de modo que ele apareça atrás da câmera, e não na frente dele.

 Nesse cenário, quando o aplicativo é executado para testá-lo, o plano de fundo é renderizado como esperado, mas um dos objetos não aparece. Usando Diagnóstico de Gráficos, você captura o problema em um log de gráficos para que você possa depurar o aplicativo. O problema tem esta aparência no aplicativo:

 ![O objeto não pode ser visto.](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")

## <a name="investigation"></a>Investigação
 Usando as ferramentas de Diagnóstico de Gráficos, você pode carregar o arquivo de log de gráficos para inspecionar os quadros que foram capturados durante o teste.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos

1. No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , carregue um log de gráficos que contém um quadro que exibe o objeto ausente. Uma nova guia log de gráficos é exibida em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Na parte superior dessa guia está a saída de destino de renderização do quadro selecionado. Na parte inferior está a **lista de quadros**, que exibe cada quadro capturado como uma imagem em miniatura.

2. Na **lista de quadros**, selecione um quadro que demonstra que o objeto não é exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, a guia log de gráficos tem esta aparência:

    ![O documento de log de gráficos no Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")

   Depois de selecionar um quadro que demonstre o problema, você pode começar a diagnosticar usando a lista de **eventos de gráficos**. A **lista de eventos gráficos** contém cada chamada à API do Direct3D que foi feita para renderizar o quadro ativo, por exemplo, chamadas à API para configurar o estado do dispositivo, para criar e atualizar buffers e para desenhar objetos que aparecem no quadro. Muitos tipos de chamadas são interessantes porque há muitas vezes (mas nem sempre) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado, por exemplo, desenhar, distribuir, copiar ou limpar chamadas. As chamadas Draw são particularmente interessantes porque cada uma representa a geometria que o aplicativo renderizado (as chamadas de expedição também podem renderizar geometry).

   Como você sabe que o objeto ausente não está sendo desenhado para o destino de renderização (nesse caso) — mas que o restante da cena é desenhado conforme o esperado — você pode usar a **lista de eventos gráficos** junto com a ferramenta de **estágios de pipeline de gráficos** para determinar qual chamada de desenho corresponde à geometria do objeto ausente. A janela **estágios de pipeline de gráficos** mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito no destino de renderização. À medida que você percorre as chamadas Draw, os estágios de pipeline são atualizados para mostrar a geometria associada a essa chamada, e a saída de destino de renderização é atualizada para mostrar o estado do destino de renderização após a conclusão da chamada.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para localizar a chamada de desenho para a geometria ausente

1. Abra a janela **lista de eventos de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **lista de eventos**.

2. Abra a janela **estágios de pipeline de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **estágios de pipeline**.

3. Conforme você percorre cada chamada de desenho na janela **lista de eventos de gráficos** , observe a janela **estágios de pipeline de gráficos** para o objeto ausente. Para facilitar isso, insira "desenhar" na caixa de **pesquisa** no canto superior direito da janela da lista de **eventos de gráficos** . Isso filtra a lista para que ela contenha apenas eventos que tenham "empate" em seus títulos.

    Na janela **estágios de pipeline de gráficos** , o estágio de **Assembler de entrada** mostra a geometria do objeto antes de sua transformação e o estágio do **sombreador de vértice** mostra o mesmo objeto depois de ser transformado. Nesse cenário, você sabe que encontrou o objeto ausente quando ele é exibido no estágio do **Assembler de entrada** e nada é exibido no estágio do **sombreador de vértice** .

   > [!NOTE]
   > Se outros estágios de geometria — por exemplo, o sombreador envoltória, o sombreador de domínio ou os estágios do sombreador de geometria, processar o objeto, poderão ser a causa do problema. Normalmente, o problema está relacionado ao estágio mais antigo no qual o resultado não é exibido ou é exibido de forma inesperada.

4. Parar quando você atingir a chamada de desenho que corresponde ao objeto ausente. Nesse cenário, a janela **estágios de pipeline de gráficos** indica que a geometria foi emitida para a GPU (indicada pela miniatura do assembler de entrada), mas não aparece no destino de renderização porque algo deu errado durante o estágio do sombreador de vértice (indicado pela miniatura do sombreador de vértice):

    ![Um evento DrawIndexed e seu efeito no pipeline](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")

   Depois de confirmar que o aplicativo emitiu uma chamada de desenho para a geometria do objeto ausente e descobriu que o problema ocorre durante o estágio do sombreador de vértice, você pode usar o depurador HLSL para examinar o sombreador de vértice e descobrir o que aconteceu com a geometria do objeto. Você pode usar o depurador HLSL para examinar o estado das variáveis HLSL durante a execução, percorrer o código HLSL e definir pontos de interrupção para ajudá-lo a diagnosticar o problema.

#### <a name="to-examine-the-vertex-shader"></a>Para examinar o sombreador de vértice

1. Iniciar a depuração do estágio do sombreador de vértice. Na janela **estágios de pipeline de gráficos** , no estágio do **sombreador de vértice** , escolha o botão **Iniciar Depuração** .

2. Como o estágio de **Assembler de entrada** parece fornecer bons dados ao sombreador de vértice e o estágio de **sombreador de vértice** parece não produzir nenhuma saída, você deseja examinar a estrutura de saída do sombreador de vértice, `output` . Ao percorrer o código HLSL, você examina mais de perto quando o `output` é modificado.

3. Na primeira vez que `output` é modificado, o membro `worldPos` é gravado nele.

    ![O valor de "output. worldPos" parece razoável](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")

    Como seu valor parece ser razoável, você continua percorrendo o código até a próxima linha que modifica `output` .

4. Na próxima vez que `output` for modificado, o membro `pos` será gravado.

    ![O valor de "output. pos" foi zerado](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")

    Desta vez, o valor do `pos` membro — todos os zeros — parece suspeito. Em seguida, você deseja determinar como `output.pos` veio ter um valor de todos os zeros.

5. Observe que `output.pos` o recebe seu valor de uma variável denominada `temp` . Na linha anterior, você verá que o valor de `temp` é o resultado da multiplicação de seu valor anterior por uma constante denominada `projection` . Você suspeita que `temp` o valor suspeito é o resultado dessa multiplicação. Quando você posiciona o ponteiro em `projection` , percebe que seu valor também é todos os zeros.

    ![A matriz de projeção contém uma transformação inadequada](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")

    Nesse cenário, o exame revela que o `temp` valor suspeito é provavelmente causado por sua multiplicação por `projection` , e como `projection` é uma constante que se destina a conter uma matriz de projeção, você sabe que ela não deve conter todos os zeros.

   Depois de determinar que a constante HLSL `projection` — passada para o sombreador pelo seu aplicativo — é a origem provável do problema, a próxima etapa é encontrar o local no código-fonte do aplicativo em que o buffer de constante é preenchido. Você pode usar a **pilha de chamadas de evento de gráficos** para encontrar esse local.

#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Para descobrir onde a constante está definida no código-fonte do seu aplicativo

1. Abra a janela **pilha de chamadas de evento de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **pilha de chamadas de evento de gráficos**.

2. Navegue até a pilha de chamadas no código-fonte do seu aplicativo. Na janela **pilha de chamadas de evento de gráficos** , escolha a chamada mais alta para ver se o buffer constante está sendo preenchido lá. Se não estiver, continue a pilha de chamadas até encontrar onde ela está sendo preenchida. Nesse cenário, você descobre que o buffer de constantes está sendo preenchido — usando a `UpdateSubresource` API do Direct3D – além da pilha de chamadas em uma função denominada `MarbleMaze::Render` , e que seu valor vem de um objeto de buffer constante chamado `m_marbleConstantBufferData` :

    ![O código que define o buffer de constante do objeto](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")

   > [!TIP]
   > Se você estiver depurando o aplicativo simultaneamente, poderá definir um ponto de interrupção nesse local e ele será atingido quando o próximo quadro for renderizado. Em seguida, você pode inspecionar os membros de `m_marbleConstantBufferData` para confirmar que o valor do `projection` membro está definido como todos os zeros quando o buffer de constante é preenchido.

   Depois de encontrar o local onde o buffer constante está sendo preenchido e descobrir que seus valores vêm da variável `m_marbleConstantBufferData` , a próxima etapa é descobrir onde o `m_marbleConstantBufferData.projection` membro está definido como todos os zeros. Você pode usar **Localizar todas as referências** para verificar rapidamente o código que altera o valor de `m_marbleConstantBufferData.projection` .

#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Para localizar onde o membro de projeção é definido no código-fonte do seu aplicativo

1. Localize referências a `m_marbleConstantBufferData.projection` . Abra o menu de atalho da variável `m_marbleConstantBufferData` e escolha **Localizar todas as referências**.

2. Para navegar até o local da linha no código-fonte do aplicativo em que o `projection` membro é modificado, escolha essa linha na janela **Localizar resultados do símbolo** . Como o primeiro resultado que modifica o membro de projeção pode não ser a causa do problema, talvez seja necessário examinar várias áreas do código-fonte do aplicativo.

   Depois de localizar o local em que o `m_marbleConstantBufferData.projection` está definido, você pode examinar o código-fonte ao redor para determinar a origem do valor incorreto. Nesse cenário, você descobre que o valor de `m_marbleConstantBufferData.projection` é definido como uma variável local que é chamada antes de ser `projection` inicializada para um valor que é fornecido pelo código `m_camera->GetProjection(&projection);` na linha seguinte.

   ![A projeção de mármore é definida antes da inicialização](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")

   Para corrigir o problema, você move a linha de código que define o valor de `m_marbleConstantBufferData.projection` após a linha que inicializa o valor da variável local `projection` .

   ![O código-fonte do C&#43;&#43; corrigido](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")

   Depois de corrigir o código, você pode reconstruí-lo e executar o aplicativo novamente para descobrir que o problema de renderização foi resolvido:

   ![O objeto no agora é exibido.](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")