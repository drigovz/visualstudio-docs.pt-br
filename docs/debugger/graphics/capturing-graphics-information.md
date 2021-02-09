---
title: Capturando informações de gráficos | Microsoft Docs
description: Capture informações de gráficos do seu aplicativo do Direct3D para que você possa usar Analisador de Gráficos do Visual Studio para diagnosticar problemas de processamento e desempenho.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 29a6371d8c49aabf27227d283ec0887f07f0c89f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876440"
---
# <a name="capturing-graphics-information"></a>Capturando informações de gráficos
Capture informações de gráficos do seu aplicativo do Direct3D para que você possa usar Analisador de Gráficos do Visual Studio para diagnosticar problemas de processamento e desempenho.

## <a name="capturing-graphics-information"></a>Capturando informações de gráficos
 A captura de informações de gráficos é um processo de duas etapas. Primeiramente, você executa o aplicativo em Diagnóstico de Gráficos e depois especifica um ou mais quadros dos quais serão capturadas informações detalhadas.

### <a name="to-run-your-app-under-graphics-diagnostics"></a>Para executar o aplicativo em Diagnóstico de Gráficos

- Na barra de menus, escolha **depurar**, **gráficos** e **Iniciar Depuração de gráficos**. (Teclado: pressione Alt+F5)

- Na barra de ferramentas de **gráficos** , escolha o botão **Iniciar Depuração de gráficos** .

  Enquanto um aplicativo estiver sendo executado no Diagnóstico de Gráficos, determinados tipos de informação de gráfico são capturados o tempo todo; isso inclui a configuração do dispositivo, a criação da cadeia de troca, a criação de recursos e objetos gráficos, bem como outros eventos importantes que afetam mais de um quadro. Ao mesmo tempo, você pode capturar informações detalhadas sobre quadros específicos; isso inclui chamadas de desenho e distribuições de sombreadores de cálculo, juntamente com os recursos e objetos Direct3D que oferecem suporte a eles.

### <a name="to-capture-a-frame"></a>Para capturar um quadro

- No Visual Studio, na barra de ferramentas de **gráficos** , clique no botão **capturar quadro** ![ícone de botão de captura de gráficos](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").

- No teclado, pressione a tecla Print Screen.

  > [!NOTE]
  > Enquanto um aplicativo estiver sendo executado em **Diagnóstico de Gráficos**, a tecla Print Screen pode ser usada apenas para capturar um quadro de informações de gráfico; ela não executa sua função normal. Isso permanece em vigor até que você pare de capturar informações de gráficos, geralmente interrompendo a depuração ou saindo do aplicativo normalmente, mesmo que outro aplicativo esteja no foco.

- Na interface de captura do Visual Studio, escolha o botão **capturar quadro** localizado abaixo da linha do tempo da **sessão de diagnóstico** ou selecione o botão grande do quadro de captura localizado abaixo da rota de **retransmissão** de **quadros por segundo** e à direita de todos os quadros capturados anteriormente. Ambos os botões estão realçados na imagem abaixo.

   ![Capture quadros usando a ferramenta uso de GPU.](media/pix_gpu_usage_tool_capture_frame.png)

   Quando estiver pronto para examinar os quadros capturados, inicie o **analisador de gráficos do Visual Studio** seguindo o **quadro...** link acima das miniaturas de imagem ou clicando duas vezes na miniatura.

  Somente quadros inteiros podem ser capturados, de modo que quando você inicia uma captura, as informações de gráfico do próximo quadro são realmente gravadas. A gravação começa logo depois que o quadro no qual você iniciou a captura é apresentado e termina quando o quadro capturado é apresentado. É possível capturar quantos quadros você desejar enquanto o aplicativo estiver em execução no Diagnóstico de Gráficos. Se você não capturar nenhum quadro, o log de elementos gráficos será descartado.

  Durante a captura de quadros, o Visual Studio exibe a janela de sessão de diagnóstico (. diagsession). Se você fechar esta janela, parar a depuração ou fechar o aplicativo, não será possível capturar mais quadros para esse log. Para capturar mais informações sobre gráficos, você precisa executar o aplicativo em Diagnóstico de Gráficos novamente para iniciar uma nova sessão de diagnóstico.

### <a name="graphics-diagnostics-capture-options"></a>Opções de captura de diagnóstico de gráficos
 Você pode configurar a captura para coletar as pilhas de chamada para todos os eventos de gráficos ou um subconjunto limitado, desabilitar a captura HUD e ativar ou desativar o modo de compatibilidade de captura.

#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Para configurar as opções de captura do diagnóstico de gráficos

1. Na barra de menus, escolha Ferramentas, Opções. A caixa de diálogo Opções é exibida.

2. Na lista da categoria opções à esquerda, escolha o Diagnóstico de Gráficos e configure as opções de Diagnóstico de Gráficos que você deseja.

     **Coletar pilhas de chamadas durante a captura (torna a captura mais lenta)** Marque esta caixa para coletar pilhas de chamadas. Por padrão, as pilhas de chamadas não são coletadas. Para capturar pilhas de chamadas, certifique-se de que a caixa de seleção **coletar pilhas de chamadas durante a captura (faz com que a captura fique mais lenta** esteja definida para habilitar a coleta e, em seguida, defina a opção **para os marcadores de empate, expedição, presente e desempenho** (padrão) para coletar somente as pilhas de chamadas mais importantes ou a opção **para tudo** para coletar todas as pilhas Para parar de coletar pilhas de chamadas mais tarde, desmarque a caixa de seleção **coletar pilhas de chamadas durante a captura (torna a captura mais lenta** .

     **Desabilitar HUD no jogo durante a captura** Marque esta caixa para desabilitar a sobreposição de HUD que um aplicativo em execução no diagnóstico de gráficos geralmente é exibido. Desmarque essa opção para exibir a sobreposição HUD.

     **Capturar no modo de compatibilidade** Marque esta caixa para capturar informações de gráficos no modo de compatibilidade. A captura no modo de compatibilidade é o padrão. No modo de compatibilidade, o Direct3D não irá relatar que a GPU é compatível com todos os recursos adicionais além daqueles definidos no nível de recurso base. Isso evita que o aplicativo sendo capturado use extensões específicas de hardware da GPU em que é capturado e garante que o log de elementos gráficos possa ser executado usando qualquer GPU compatível com o mesmo nível de recurso ou superior. Desmarque essa caixa para desabilitar o modo de compatibilidade. Os logs capturados com o modo de compatibilidade desabilitado não conseguirão reproduzir em nenhuma GPU que não seja compatível com os mesmos recursos adicionais que foram usados pelo aplicativo durante a captura.

     **Parar captura se forem encontrados erros de camadas do SDK** Marque esta caixa para parar a captura imediatamente se forem encontrados erros.

## <a name="capturing-graphics-information-remotely"></a>Capturando informações de gráficos remotamente
 As informações de gráficos podem ser capturadas de um aplicativo que está em execução no computador local, de um dispositivo ou computador remoto. A captura remota tem suporte em computadores com [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] e dispositivos com [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]. Para capturar informações de gráficos de um aplicativo que está em execução remotamente, configure seu projeto para depuração remota e execute o aplicativo em Diagnóstico de Gráficos, como descrito anteriormente. O aplicativo é executado no computador remoto e as informações de gráficos capturadas são gravadas no computador de desenvolvimento.

 Como você configura o projeto para depuração remota depende do tipo de aplicativo que está sendo desenvolvido e da linguagem de programação que está sendo usada. Para obter informações sobre como configurar a depuração remota para um aplicativo UWP, consulte [executar aplicativos UWP em um computador remoto](../run-windows-store-apps-on-a-remote-machine.md). Para obter informações sobre como configurar a depuração remota para um aplicativo de área de trabalho do Windows, consulte [depuração remota](../remote-debugging.md).

 Posteriormente, você pode usar um dispositivo ou computador remoto para reproduzir informações de gráficos, independentemente de onde as informações foram capturadas. Para obter mais informações, consulte [como alterar o computador de reprodução de diagnóstico de gráficos](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="capturing-graphics-information-from-the-command-line"></a>Captura de informações de elementos gráficos da linha de comando
 Informações de gráficos poderão ser capturadas em um aplicativo usando uma ferramenta de linha de comando. Essa ferramenta, DXCap.exe, pode capturar e reproduzir rapidamente informações de gráficos sem usar o Visual Studio ou a captura programática. Em específico, você pode usar o DXCap.exe para automação ou em um ambiente de teste. Para obter mais informações sobre DXCap.exe, consulte [ferramenta de captura de linha de comando](command-line-capture-tool.md)

## <a name="see-also"></a>Confira também
- [Passo a passo: Capturando informações de gráficos](walkthrough-capturing-graphics-information.md)