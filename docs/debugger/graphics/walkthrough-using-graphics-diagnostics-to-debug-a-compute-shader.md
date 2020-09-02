---
title: Depuração do sombreador de computação usando o diagnóstico de gráficos
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19ae8472aaafbad1a04485ff2e3a2637f345bc00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66262861"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Passo a passo: Como usar o Diagnóstico de Gráficos para depurar um sombreador de computação
Este tutorial demonstra como usar as ferramentas de Diagnóstico de Gráficos do Visual Studio para investigar um sombreador de computação que gera resultados incorretos.

 Este tutorial ilustra essas tarefas:

- Usando a **lista de eventos gráficos** para localizar possíveis fontes do problema.

- Usando a **pilha de chamadas de evento de gráficos** para determinar qual sombreador de computação é executado por um `Dispatch` evento DirectCompute.

- Usando a janela **estágios de pipeline de gráficos** e o depurador HLSL para examinar o sombreador de computação que é a origem do problema.

## <a name="scenario"></a>Cenário
 Nesse cenário, você escreveu uma simulação de fluidos que usa o DirectCompute para executar as partes mais computadas da atualização de simulação. Quando o aplicativo é executado, a renderização do conjunto de aplicativos e da interface do usuário parece correta, mas a simulação não se comporta conforme o esperado. Usando Diagnóstico de Gráficos, você pode capturar o problema para um log de gráficos para que você possa depurar o aplicativo. O problema tem esta aparência no aplicativo:

 ![O fluido simulado se comporta incorretamente.](media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")

 Para obter informações sobre como capturar problemas gráficos em um log de gráficos, consulte [capturando informações de gráficos](capturing-graphics-information.md).

## <a name="investigation"></a>Investigação
 Você pode usar as ferramentas de Diagnóstico de Gráficos para carregar o arquivo de log de gráficos para que você possa inspecionar os quadros capturados.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar um quadro em um log de gráficos

1. No Visual Studio, carregue um log de gráficos que contém um quadro que exibe os resultados de simulação incorretos. Uma nova guia Diagnóstico de Gráficos aparece no Visual Studio. Na parte superior dessa guia está a saída de destino de renderização do quadro selecionado. Na parte inferior está a **lista de quadros**, que exibe uma miniatura de cada quadro capturado.

2. Na **lista de quadros**, selecione um quadro que demonstre o comportamento de simulação incorreto. Embora o erro pareça estar no código de simulação e não no código de renderização, você ainda precisa escolher um quadro porque os eventos DirectCompute são capturados de quadro por quadro, juntamente com os eventos do Direct3D. Nesse cenário, a guia log de gráficos tem esta aparência:

    ![O documento de log de gráficos no Visual Studio.](media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")

   Depois de selecionar um quadro que demonstre o problema, você pode usar a **lista de eventos de gráficos** para diagnosticar. A **lista de eventos de gráficos** contém um evento para cada chamada de DirectCompute e chamada de API de Direct3D que foi feita durante o quadro ativo — por exemplo, chamadas à API para executar uma computação na GPU ou para renderizar o conjunto de imagem ou a interface do usuário. Nesse caso, estamos interessados em `Dispatch` eventos que representam partes da simulação que são executadas na GPU.

#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Para localizar o evento de expedição para a atualização de simulação

1. Na barra de ferramentas **diagnóstico de gráficos** , escolha **lista de eventos** para abrir a janela lista de eventos de **gráficos** .

2. Inspecione a **lista de eventos de gráficos** para o evento de desenho que renderiza o conjunto de recursos. Para facilitar isso, insira `Draw` na caixa de **pesquisa** no canto superior direito da janela da lista de **eventos de gráficos** . Isso filtra a lista para que ela contenha apenas eventos que tenham "empate" em seus títulos. Nesse cenário, você descobre que esses eventos de desenho ocorreram:

    ![A lista de eventos &#40;EL&#41; mostra os eventos de desenho.](media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")

3. Percorra cada evento de desenho enquanto observa o destino de renderização na guia documento de log de gráficos.

4. Parar quando o destino de renderização exibir primeiro o conjunto de os renderizados. Nesse cenário, o conjunto de eventos é renderizado no primeiro evento de desenho. O erro na simulação é mostrado:

    ![Esse evento de desenho renderiza o conjunto de dados de simulação.](media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")

5. Agora, inspecione a **lista de eventos de gráficos** para o `Dispatch` evento que atualiza a simulação. Como é provável que a simulação seja atualizada antes de ser renderizada, você pode se concentrar primeiro nos `Dispatch` eventos que ocorrem antes do evento de desenho que renderiza os resultados. Para facilitar, modifique a caixa de **pesquisa** para leitura `Draw;Dispatch;CSSetShader(` . Isso filtra a lista para que ela também contenha `Dispatch` eventos e, `CSSetShader` além de desenhar eventos. Nesse cenário, você descobre que vários `Dispatch` eventos ocorreram antes do evento de empate:

    ![O EL mostra os eventos Draw, expedição e CSSetShader](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")

   Agora que você sabe quais poucos eventos possivelmente muitos `Dispatch` podem corresponder ao problema, você pode examiná-los mais detalhadamente.

#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Para determinar qual sombreador de computação é executado por uma chamada de expedição

1. Na barra de ferramentas **diagnóstico de gráficos** , escolha **pilha de chamadas de evento** para abrir a janela de pilha de chamadas de evento de **gráficos** .

2. A partir do evento de desenho que renderiza os resultados da simulação, mova-se para trás por cada `CSSetShader` evento anterior. Em seguida, na janela **pilha de chamadas de evento de gráficos** , escolha a função mais alta para navegar até o site de chamada. No site de chamada, você pode usar o primeiro parâmetro da chamada de função [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) para determinar qual sombreador de computação é executado pelo próximo `Dispatch` evento.

   Nesse cenário, há três pares de `CSSetShader` `Dispatch` eventos e em cada quadro. Trabalhando retroativamente, o terceiro par representa a etapa de integração (onde as partículas de fluidos são realmente movidas), o segundo par representa a etapa de cálculo de força (em que as forças que afetam cada partícula são calculadas) e o primeiro par representa a etapa de cálculo de densidade.

#### <a name="to-debug-the-compute-shader"></a>Para depurar o sombreador de computação

1. Na barra de ferramentas **diagnóstico de gráficos** , escolha **estágios de pipeline** para abrir a janela estágios de pipeline de **gráficos** .

2. Selecione o terceiro `Dispatch` evento (aquele que precede imediatamente o evento de desenho) e, na janela estágios de **pipeline de gráficos** , no estágio do **sombreador de computação** , escolha **Iniciar Depuração**.

    ![Selecionando o terceiro evento de expedição no EL.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")

    O depurador HLSL é iniciado no sombreador que executa a etapa de integração.

3. Examine o código-fonte do sombreador de computação para a etapa de integração para pesquisar a origem do erro. Ao usar Diagnóstico de Gráficos para depurar o código do sombreador de computação HLSL, você pode percorrer o código e usar outras ferramentas de depuração conhecidas, como as janelas de inspeção. Nesse cenário, você determina que não parece haver um erro no sombreador de computação que executa a etapa de integração.

    ![Depurando o sombreador de computação IntegrateCS.](media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")

4. Para parar a depuração do sombreador de computação, na barra de ferramentas **depurar** , escolha **parar depuração** (teclado: Shift + F5).

5. Em seguida, selecione o segundo `Dispatch` evento e inicie a depuração do sombreador de computação da mesma forma que fazia na etapa anterior.

    ![Selecionando o segundo evento de expedição no EL.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")

    O depurador HLSL é iniciado no sombreador que calcula as forças que agem em cada partícula fluida.

6. Examine o código-fonte do sombreador de computação para a etapa de cálculo forçado. Nesse cenário, você determina que a origem do erro está aqui.

    ![Depurando o ForceCS&#95;sombreador de computação simples.](media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")

   Depois de determinar o local do erro, você pode parar a depuração e modificar o código-fonte do sombreador de computação para calcular corretamente a distância entre as partículas de interação. Nesse cenário, basta alterar a linha `float2 diff = N_position + P_position;` para `float2 diff = N_position - P_position;` :

   ![A computação corrigida&#45;código do sombreador.](media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")

   Nesse cenário, como os sombreadores de computação são compilados em tempo de execução, você pode apenas reiniciar o aplicativo depois de fazer as alterações para observar como eles afetam a simulação. Você não precisa recompilar o aplicativo. Ao executar o aplicativo, você descobre que a simulação agora se comporta corretamente.

   ![O fluido simulado comporta-se corretamente.](media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")