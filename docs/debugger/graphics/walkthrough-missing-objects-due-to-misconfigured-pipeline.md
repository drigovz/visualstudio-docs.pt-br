---
title: Objetos ausentes devido a pipeline configurado incorretamente
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64c00c10b8b7207e1162aa0041145000126fde87
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189843"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Passo a passo: Objetos ausentes devido a configuração incorreta do pipeline
Este tutorial demonstra como usar as [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para investigar um objeto ausente devido a um sombreador de pixel de desdefinição.

 Este tutorial ilustra essas tarefas:

- Usando a **lista de eventos gráficos** para localizar possíveis fontes do problema.

- Usando a janela **estágios de pipeline de gráficos** para examinar o efeito da chamada à API do `DrawIndexed` Direct3D.

- Inspecionando o contexto do dispositivo para confirmar se um estágio do sombreador não foi definido.

- Usando a janela **estágios de pipeline de gráficos** junto com a pilha de chamadas de evento de **gráficos** para ajudar a localizar a origem do sombreador de pixel de desdefinição.

## <a name="scenario"></a>Cenário
 Quando um objeto está ausente em um aplicativo 3D, às vezes é porque um dos estágios do sombreador não está definido antes de o objeto ser renderizado. Em aplicativos que têm necessidades de renderização simples, a origem desse erro geralmente está localizada em algum lugar na pilha de chamadas da chamada de desenho do objeto. No entanto, como uma otimização, alguns aplicativos agrupam em lote objetos que têm programas de sombreador, texturas ou outros dados em comum para minimizar a sobrecarga de alteração de estado. Nesses aplicativos, a origem do erro pode ser incluída no sistema de envio em lote, em vez de ser localizada na pilha de chamadas da chamada de desenho. O cenário neste tutorial demonstra um aplicativo que tem necessidades de processamento simples e, portanto, a origem do erro pode ser encontrada na pilha de chamadas.

 Nesse cenário, quando o aplicativo é executado para testá-lo, o plano de fundo é renderizado como esperado, mas um dos objetos não aparece. Usando Diagnóstico de Gráficos, você captura o problema em um log de gráficos para que você possa depurar o aplicativo. O problema tem esta aparência no aplicativo:

 ![O objeto não pode ser visto](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")

## <a name="investigation"></a>Investigação
 Usando as ferramentas de Diagnóstico de Gráficos, você pode carregar o documento de log de gráficos para inspecionar os quadros que foram capturados durante o teste.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos

1. No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , carregue um documento de log de gráficos que contém um quadro que exibe o objeto ausente. Uma nova guia log de gráficos é exibida em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Na parte superior dessa guia está a saída de destino de renderização do quadro selecionado. Na parte inferior está a **lista de quadros**, que exibe cada quadro capturado como uma imagem em miniatura.

2. Na **lista de quadros**, selecione um quadro que demonstra que o objeto não é exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, a guia log de gráficos tem esta aparência:

    ![O documento de log de gráficos no Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")

   Depois de selecionar um quadro que demonstre o problema, você pode começar a diagnosticar usando a **lista de eventos de gráficos**. A **lista de eventos de gráficos** contém cada chamada à API do Direct3D que foi feita para renderizar o quadro ativo, por exemplo, para configurar o estado do dispositivo, para criar e atualizar buffers e para desenhar objetos que aparecem no quadro. Muitos tipos de chamadas — por exemplo, empate, expedição, cópia ou limpeza de chamadas — são interessantes porque há muitas vezes (mas nem sempre) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado. As chamadas Draw são particularmente interessantes porque cada uma representa a geometria que o aplicativo renderiza.

   Como você sabe que o destino de renderização não contém o objeto ausente, mas também que não parece haver outros erros, você pode usar a **lista de eventos gráficos** junto com a ferramenta de **estágios de pipeline de gráficos** para determinar qual chamada de desenho corresponde à geometria do objeto ausente. A janela **estágios de pipeline de gráficos** mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito no destino de renderização. À medida que você percorre as chamadas de desenho, os estágios de pipeline são atualizados para mostrar a geometria associada a cada chamada conforme ele flui em cada estágio habilitado e a saída de destino de renderização é atualizada para mostrar o estado do destino de renderização após a conclusão da chamada.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para localizar a chamada de desenho para a geometria ausente

1. Abra a janela **lista de eventos de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **lista de eventos**.

2. Abra a janela **estágios de pipeline de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **estágios de pipeline**.

3. Conforme você percorre cada chamada de desenho na janela **lista de eventos de gráficos** , observe a janela **estágios de pipeline de gráficos** para o objeto ausente. Para facilitar isso, insira "desenhar" na caixa de **pesquisa** no canto superior direito da janela da lista de **eventos de gráficos** . Isso filtra a lista para que ela contenha apenas eventos que tenham "empate" em seus títulos.

    Na janela **estágios de pipeline de gráficos** , o estágio de **Assembler de entrada** mostra a geometria do objeto antes de ser transformada e o estágio do **sombreador de vértice** mostra o mesmo objeto após sua transformação. Nesse cenário, observe que a janela **estágios de pipeline de gráficos** mostra as fases de **Assembler de entrada** e  **sombreador de vértice** , mas não o estágio **pixel shader** para uma das chamadas Draw.

   > [!NOTE]
   > Se outros estágios de pipeline, por exemplo, o sombreador envoltória, o sombreador de domínio ou os estágios do sombreador de geometria, processar o objeto, qualquer um deles poderá ser a causa do problema. Normalmente, o problema está relacionado ao estágio mais antigo no qual o resultado não é exibido ou é exibido de forma inesperada.

4. Parar quando você atingir a chamada de desenho que corresponde ao objeto ausente. Nesse cenário, a janela **estágios de pipeline de gráficos** indica que a geometria foi emitida para a GPU (indicada pela presença do estágio de **Assembler de entrada** ) e transformada (indicada pelo estágio de **sombreador de vértice** ), mas não aparece no destino de renderização porque não parece haver um sombreador de pixel ativo (indicado pela ausência do estágio **pixel shader** ). Nesse cenário, você pode até ver a silhueta do objeto ausente no estágio de **fusão de saída** :

    ![Um evento DrawIndexed e seu efeito no pipeline](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")

   Depois de confirmar que o aplicativo emitiu uma chamada de desenho para a geometria do objeto ausente e descobriu que o estágio do sombreador de pixel estava inativo, você pode examinar o estado do dispositivo para confirmar suas descobertas. Você pode usar a **tabela de objetos gráficos** para examinar o contexto do dispositivo e outros dados de objeto do Direct3D.

#### <a name="to-examine-device-context"></a>Para examinar o contexto do dispositivo

1. Abra o **contexto do dispositivo D3D11**. Na janela **estágios de pipeline de gráficos** , escolha o link **ID3D11DeviceContext** que faz parte da `DrawIndexed` chamada que é exibida na parte superior da janela.

2. Examine o estado do dispositivo exibido na guia **contexto do dispositivo D3D11** para confirmar que nenhum sombreador de pixel estava ativo durante a chamada de desenho. Nesse cenário, as **informações gerais do sombreador**– exibidas em **estado do sombreador de pixel**— indica que o sombreador é **nulo**:

    ![O contexto do dispositivo D3D 11 mostra o estado do sombreador de pixel](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")

   Depois de confirmar que o sombreador de pixel foi definido como nulo pelo seu aplicativo, a próxima etapa é encontrar o local no código-fonte do aplicativo em que o sombreador está definido. Você pode usar a **lista de eventos gráficos** junto com a **pilha de chamadas de evento de gráficos** para localizar esse local.

#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Para descobrir onde o sombreador de pixel está definido no código-fonte do seu aplicativo

1. Localize a `PSSetShader` chamada que corresponde ao objeto ausente. Na janela **lista de eventos de gráficos** , digite "Draw; PSSetShader "na caixa de **pesquisa** no canto superior direito da janela da **lista de eventos de gráficos** . Isso filtra a lista para que ela contenha apenas eventos "PSSetShader" e eventos que tenham "empate" em seus títulos. Escolha a primeira `PSSetShader` chamada que aparece antes da chamada de desenho do objeto ausente.

   > [!NOTE]
   > `PSSetShader` não aparecerá na janela da **lista de eventos de gráficos** se ela não tiver sido definida durante esse quadro. Geralmente isso ocorrerá apenas se apenas um sombreador de pixel for usado para todos os objetos ou se a `PSSetShader` chamada tiver sido ignorada involuntariamente durante esse quadro. Em ambos os casos, recomendamos que você pesquise o código-fonte do aplicativo em busca de `PSSetShader` chamadas e use técnicas de depuração tradicionais para examinar o comportamento dessas chamadas.

2. Abra a janela **pilha de chamadas de evento de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **pilha de chamadas de evento de gráficos**.

3. Use a pilha de chamadas para localizar a `PSSetShader` chamada no código-fonte do seu aplicativo. Na janela **pilha de chamadas de evento de gráficos** , escolha a chamada mais alta e examine o valor para o qual o sombreador de pixel está sendo definido. O sombreador de pixel pode ser definido diretamente como nulo, ou o valor nulo pode ocorrer devido a um argumento que foi passado para a função ou outro Estado. Se não estiver definido diretamente, você poderá localizar a origem do valor nulo em algum lugar da pilha de chamadas. Nesse cenário, você descobre que o sombreador de pixel está sendo definido diretamente para `nullptr` na função mais alta, chamada `CubeRenderer::Render` :

    ![O código que não inicializa o sombreador de pixel](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")

   > [!NOTE]
   > Se você não conseguir localizar a origem do valor nulo apenas examinando a pilha de chamadas, recomendamos que você defina um ponto de interrupção condicional na `PSSetShader` chamada, de modo que a execução do programa seja interrompida quando o sombreador de pixel for definido como nulo. Em seguida, reinicie o aplicativo no modo de depuração e use as técnicas de depuração tradicionais para localizar a origem do valor nulo.

   Para corrigir o problema, atribua o sombreador de pixel correto usando o primeiro parâmetro da `ID3D11DeviceContext::PSSetShader` chamada à API.

   ![O código-fonte do C&#43;&#43; corrigido](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")

   Depois de corrigir o código, você pode reconstruí-lo e executar o aplicativo novamente para verificar se o problema de renderização foi resolvido:

   ![O objeto agora é exibido](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")