---
title: 'Walkthrough: objetos ausentes devido ao estado do dispositivo | Microsoft Docs'
description: Siga uma investigação que localize um estado de dispositivo configurado incorretamente. Ele mostra o uso de lista de eventos gráficos, estágios de pipeline de gráficos e histórico de pixels gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c29e240d4be2f66fb0684bf5372d59fe5d4d825a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995051"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Passo a passo: Objetos ausentes devido ao estado do dispositivo
Este tutorial demonstra como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnóstico de gráficos para investigar um objeto ausente devido ao estado do dispositivo configurado incorretamente.

 Este guia passo a passo demonstra como:

- Use a **lista de eventos gráficos** para localizar possíveis fontes do problema.

- Use a janela **estágios de pipeline de gráficos** para verificar o efeito das chamadas à API do `DrawIndexed` Direct3D.

- Use a janela **histórico de pixels de gráficos** para localizar o problema mais especificamente.

- Inspecione o estado do dispositivo em busca de possíveis problemas ou configurações incorretas.

## <a name="scenario"></a>Cenário
 Um dos motivos pelos quais os objetos podem não aparecer onde eles são esperados em um aplicativo 3D é uma configuração incorreta do dispositivo de gráficos que faz com que os objetos sejam excluídos da renderização — por exemplo, quando a ordem de enrolagem faz com que os triângulos sejam procurados em erro ou quando a função de teste de profundidade faz com que todos os pixels no objeto sejam rejeitados

 No cenário que é descrito neste guia de explicação, você acabou de atingir a primeira etapa no desenvolvimento do seu aplicativo 3D e está pronto para testá-lo pela primeira vez. No entanto, quando você executa o aplicativo, apenas a interface do usuário é renderizada na tela. Usando Diagnóstico de Gráficos, você captura o problema em um arquivo de log de gráficos para que você possa depurar o aplicativo. O problema tem esta aparência no aplicativo:

 ![O aplicativo antes do problema ser corrigido](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")

 Para obter informações sobre como capturar problemas gráficos em um log de gráficos, consulte [capturando informações de gráficos](capturing-graphics-information.md).

## <a name="investigation"></a>Investigação
 Usando as ferramentas de Diagnóstico de Gráficos, você pode carregar o arquivo de log de gráficos para inspecionar os quadros que foram capturados durante o teste.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos

1. No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , carregue um log de gráficos que contém um quadro que exibe o modelo ausente. Uma nova guia Diagnóstico de Gráficos aparece em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Na parte superior dessa guia está a saída de destino de renderização do quadro selecionado. Na parte inferior está a **lista de quadros**, que exibe cada quadro capturado como uma imagem em miniatura.

2. Na **lista de quadros**, selecione um quadro que demonstra que o modelo não é exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, a guia log de gráficos tem esta aparência:

    ![A guia. vsglog framebuffer visualização e lista de quadros](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")

   Depois de selecionar um quadro que demonstre o problema, você pode usar a **lista de eventos de gráficos** para diagnosticar. A **lista de eventos gráficos** contém cada chamada à API do Direct3D que foi feita para renderizar o quadro ativo, por exemplo, chamadas à API para configurar o estado do dispositivo, para criar e atualizar buffers e para desenhar objetos que aparecem no quadro. Muitos tipos de chamadas são interessantes porque há muitas vezes (mas nem sempre) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado, por exemplo, desenhar, distribuir, copiar ou limpar chamadas. As chamadas Draw são particularmente interessantes porque cada uma representa a geometria que o aplicativo renderizado (as chamadas de expedição também podem renderizar geometry).

#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Para garantir que as chamadas de desenho estejam sendo feitas

1. Abra a janela **lista de eventos de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **lista de eventos**.

2. Inspecione a **lista de eventos de gráficos** para chamadas de desenho. Para facilitar isso, insira "desenhar" na caixa de **pesquisa** no canto superior direito da janela da lista de **eventos de gráficos** . Isso filtra a lista para que ela contenha apenas eventos que tenham "empate" em seus títulos. Nesse cenário, você descobre que várias chamadas de desenho foram feitas:

    ![Lista de eventos de gráficos mostrando eventos capturados](media/vsg_walkthru1_.png "vsg_walkthru1_")

   Depois de confirmar que as chamadas de desenho estão sendo feitas, você pode determinar qual delas corresponde à geometria ausente. Como você sabe que a geometria ausente não está sendo desenhada para o destino de renderização (nesse caso), você pode usar a janela **estágios de pipeline de gráficos** para determinar qual chamada de desenho corresponde à geometria ausente. A janela **estágios de pipeline de gráficos** mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito no destino de renderização. À medida que você percorre as chamadas Draw, os estágios de pipeline são atualizados para mostrar a geometria associada a essa chamada, e a saída de destino de renderização é atualizada para mostrar o estado do destino de renderização após a conclusão da chamada.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para localizar a chamada de desenho para a geometria ausente

1. Abra a janela **estágios de pipeline de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **estágios de pipeline**.

2. Percorrer cada chamada de desenho ao assistir à janela de **estágios de pipeline de gráficos** para o modelo ausente. O estágio de **Assembler de entrada** mostra os dados de modelo brutos. O estágio de **sombreador de vértice** mostra os dados de modelo transformados. O estágio **pixel shader** mostra a saída do sombreador de pixel. A fase de **mesclagem de saída** mostra o destino de renderização mesclado dessa chamada de desenho e todas as chamadas de desenho anteriores.

3. Pare quando você tiver atingido a chamada de desenho que corresponde ao modelo ausente. Nesse cenário, a janela **estágios de pipeline de gráficos** indica que a geometria foi renderizada, mas não apareceu no destino de renderização:

    ![Visualizador de pipeline mostrando o objeto ausente](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")

   Depois de confirmar que o aplicativo renderiza a geometria ausente e que você localiza a chamada de desenho correspondente, você pode selecionar uma parte da saída de destino de renderização que deve mostrar a geometria ausente e, em seguida, usar a janela de **histórico de pixels de gráficos** para descobrir por que os pixels foram excluídos. O histórico de pixel contém uma lista de cada chamada de desenho que pode ter tido um efeito em um pixel específico. Cada chamada de desenho na janela de **histórico de pixels de gráficos** é identificada por um número que também é exibido na janela lista de eventos de **gráficos** . Isso ajuda a confirmar se o pixel deve exibir a geometria ausente e descobrir por que o pixel foi excluído

#### <a name="to-determine-why-the-pixel-was-excluded"></a>Para determinar por que o pixel foi excluído

1. Abra a janela **histórico de pixels de gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **histórico de pixel**.

2. Com base na miniatura do **sombreador de pixel** , selecione um pixel na saída framebuffer que deve conter uma parte da geometria ausente. Nesse cenário, a saída do sombreador de pixel deve abranger a maior parte do destino de renderização; Depois que um pixel é selecionado, a janela de **histórico de pixels de gráficos** tem a seguinte aparência:

    ![Janela de histórico de pixel mostrando chamadas de desenho relacionadas](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")

3. Confirme se o pixel de destino de renderização selecionado contém uma parte da geometria combinando o número da chamada de desenho que você está inspecionando (na janela **lista de eventos gráficos** ) para uma das chamadas de desenho na janela **histórico de pixels de gráficos** . Se nenhuma das chamadas na janela de **histórico de pixels de gráficos** corresponder à chamada de desenho que você está inspecionando, repita essas etapas (exceto a etapa 1) até encontrar uma correspondência. Nesse cenário, a chamada de desenho correspondente tem esta aparência:

    ![Janela Histórico de pixel mostrando informações de fragmento](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")

4. Quando encontrar uma correspondência, expanda a chamada de desenho correspondente na janela **histórico de pixels de gráficos** e confirme se o pixel foi excluído. Cada chamada de desenho na janela de **histórico de pixels de gráficos** corresponde a um ou mais primitivos geométricos (pontos, linhas ou triângulos) que interseccionaram esse pixel como resultado da geometria do objeto correspondente. Cada interseção pode contribuir para a cor final do pixel. Um primitivo que é excluído porque falhou, o teste de profundidade é representado por um ícone que mostra a letra Z em uma seta que se inclina para baixo da esquerda para a direita.

5. Expanda um primitivo excluído para examinar melhor o estado que fez com que ele fosse excluído. No grupo de **fusão de saída** , mova o ponteiro sobre o **resultado**. Uma dica de ferramenta indica por que o primitivo foi excluído. Nesse cenário, o exame revela que o primitivo foi excluído porque falhou no teste de profundidade e, portanto, não contribuiu para a cor final do pixel.

   Depois de determinar que a geometria não aparece porque seus primitivos falharam no teste de profundidade, você pode suspeitar que esse problema está relacionado ao estado do dispositivo configurado incorretamente. O estado do dispositivo e outros dados de objeto do Direct3D podem ser examinados usando a **tabela de objetos gráficos**.

#### <a name="to-examine-device-state"></a>Para examinar o estado do dispositivo

1. Abra a janela **tabela de objetos gráficos** . Na barra de ferramentas **diagnóstico de gráficos** , escolha **tabela de objetos**.

2. Localize o objeto de **dispositivo d3d10** na **tabela de objetos gráficos** e, em seguida, abra o objeto de **dispositivo d3d10** . Uma nova guia **dispositivo d3d10** é aberta no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Para tornar isso mais fácil, você pode classificar a **tabela de objetos gráficos** por **tipo**:

    ![Tabela de objetos gráficos e estado de dispositivo relacionado](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")

3. Examine o estado do dispositivo exibido na guia **dispositivo d3d10** para obter possíveis problemas. Como a geometria não aparece porque seus primitivos falharam no teste de profundidade, você pode se concentrar no estado do dispositivo, como o estêncil de profundidade, que afeta o teste de profundidade. Nesse cenário, a **Descrição do estêncil de profundidade** (em estado de fusão de **saída**) contém um valor incomum para o membro da **função de profundidade** , `D3D10_COMPARISON_GREATER` :

    ![Janela do dispositivo D3D10 mostrando informações de estêncil de profundidade](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")

   Depois de determinar que a causa do problema de renderização pode ser uma função de profundidade configurada incorretamente, você pode usar essas informações junto com seu conhecimento do código para localizar onde a função de profundidade foi definida de forma incorreta e, em seguida, corrigir o problema. Se você não estiver familiarizado com o código, poderá procurar o problema usando as pistas coletadas durante a depuração — por exemplo, com base na descrição do estêncil de **profundidade** nesse cenário, você poderá pesquisar o código em busca de palavras como "profundidade" ou "maior". Depois de corrigir o código, recompile-o e execute o aplicativo novamente para descobrir que o problema de renderização foi resolvido:

   ![Aplicativo após o problema ser corrigido](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")