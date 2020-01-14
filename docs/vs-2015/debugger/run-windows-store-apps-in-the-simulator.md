---
title: Executar aplicativos da Windows Store no simulador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d072f54dfe351d54e3e115dca7a91bec77fbb9e6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844924"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Executar aplicativos da Windows Store no simulador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O simulador do Visual Studio para aplicativos da Windows Store é um aplicativo da área de trabalho que simula um aplicativo da Windows Store. Você pode executar aplicativos e simular eventos comuns de toque e rotação em seu computador de desenvolvimento. Você também pode escolher o tamanho da tela física e a resolução que deseja emular e simular as propriedades de conexão de rede.  
  
 O simulador fornece um ambiente no qual você pode criar, desenvolver, depurar e testar aplicativos da Windows Store. No entanto, antes de publicar um aplicativo na Windows Store, convém testá-lo em um dispositivo real.  
  
 O simulador do Visual Studio para aplicativos da Windows Store não é executado em um ambiente isolado no computador local. Portanto, os erros que ocorrem no simulador, como um erro não recuperável geral do sistema, também podem afetar o computador inteiro.  
  
 Consulte [executar Windows Phone aplicativos no emulador](../debugger/run-windows-phone-apps-in-the-emulator.md) para obter Windows Phone informações.  
  
> [!IMPORTANT]
> O simulador do Visual Studio 2015 não inclui o botão de localização geográfica. Isso ocorre porque o simulador do Windows 10 não inclui a simulação de geolocalização. Se você precisar fazer esse tipo de simulação, poderá usar o simulador de Visual Studio 2013 em Windows 8.1 ou em sistemas operacionais anteriores.  
  
## <a name="BKMK_Set_the_simulator_as_the_target"></a> Definir o simulador como o destino  
 Para executar seu aplicativo da Windows Store no simulador, selecione **simulador** na lista suspensa ao lado do botão **Iniciar Depuração** na barra de ferramentas **padrão** do depurador.  
  
 ![Executando no simulador](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
## <a name="BKMK_Choose_an_interaction_mode"></a> Escolher um modo de interação  
 Você pode escolher os seguintes modos de interação  
  
- ![Botão de modo do mouse](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") Modo de mouse: define o modo de interação com gestos do mouse. Esses gestos incluem clicar, clicar duas vezes e arrastar.  
  
- ![Botão iniciar emulação de toque](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Iniciar emulação de toque: define o modo de interação para gestos de toque de um único dedo. Os eventos desse tipo incluem tocar, arrastar e passar o dedo.  
  
     ![Destino de um dedo de simulador](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") O ícone de destino único indica o local dos eventos no simulador. Use o mouse para posicionar o ponteiro.  
  
     ![Destino de toque de um dedo](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") Pressione o botão esquerdo do mouse para ativar o modo de toque. Por exemplo, clique no botão para simular um gesto de tocar, ou pressione e segure o botão enquanto você arrasta ou passa o dedo.  
  
## <a name="pinch-and-zoom"></a>Aperto e zoom  
 Defina o modo de interação como sendo gestos de aperto e zoom com dois dedos.  
  
- ![Destino de dois dedos de simulador](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  

  - {1&gt;O ícone de alvo duplo indica o local de dois dedos na tela do dispositivo. &lt;1}  

  - {1&gt;Mova o mouse para posicionar os ícones sobre o objeto na tela do dispositivo.&lt;1}  

  - {1&gt;Gire a roda do mouse para trás ou para a frente a fim de alterar a distância simulada dos dois dedos antes de apertar ou aplicar zoom.&lt;1}  

- ![Pinçar, aplicar zoom e girar destinos](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  

  - {1&gt;Pressione o botão esquerdo e gire a roda para trás (na sua direção) a fim de ampliar a exibição (aperto).&lt;1}  

  - {1&gt;Pressione o botão esquerdo e gire a roda do mouse para a frente (afastada de você) a fim de reduzir a exibição (zoom).&lt;1}  
  
## <a name="object-rotation"></a>Rotação de objeto  
 O botão **girar emulação de toque** define o modo de interação com gestos de rotação usando dois dedos.  
  
- {1&gt;Mova o mouse para posicionar os ícones sobre o objeto na tela do dispositivo.&lt;1}  
  
  - {1&gt;Gire a roda do mouse para trás ou para frente para alterar a orientação simulada dos dois dedos antes de girar o objeto.&lt;1}  

- Pressione o botão esquerdo e gire a roda para trás (na sua direção) a fim de girar o objeto no sentido anti-horário. Conforme você gira a roda do mouse, um dos dois ícones de alvo gira em torno do outro para indicar o tamanho relativo da rotação.  

  - {1&gt;Pressione o botão esquerdo e gire a roda do mouse para a frente (afastada de você) a fim de girar o objeto no sentido horário.&lt;1}  

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Habilitar ou desabilitar o modo Sempre visível  
 {1&gt;Você pode configurar a janela do simulador para ficar sempre por cima das outras janelas.&lt;1} O botão **alternar janela superior** habilita ou desabilita o modo **superior do Always on** na janela do simulador.  
  
## <a name="BKMK_Change_the_device_orientation"></a> Alterar a orientação do dispositivo  
 {1&gt;Você pode alternar a orientação do dispositivo entre retrato e paisagem girando o simulador 90 graus em qualquer direção.&lt;1}  
  
> [!NOTE]
> O simulador não respeita a propriedade [DisplayProperties.AutoRotationPreferences](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayproperties.autorotationpreferences.aspx) de um projeto. Por exemplo, se o projeto define a orientação como `Landscape` e você gira o simulador até a orientação retrato, a imagem de exibição do simulador também é girada e redimensionada. Teste essas configurações em um dispositivo real.  
  
> [!NOTE]
> Se você gira o simulador de modo que uma borda dele fique maior do que a tela em que ele é exibido, o simulador será automaticamente redimensionado para caber na tela. O simulador não é redimensionado para o tamanho original se você o gira novamente.  
  
## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Alterar o tamanho e a resolução de tela simulados  
 Para alterar o tamanho e a resolução de tela simulados, escolha o botão **Alterar Resolução** na paleta e escolha um novo tamanho e uma nova resolução na lista.  
  
 O tamanho e a resolução da tela são listados como *Largura da tela em polegadas, largura em pixel X altura em pixel*. Observe que tanto o tamanho como a resolução da tela são simulados. As coordenadas de local no simulador são convertidas nas coordenadas do tamanho e da resolução do dispositivo selecionado.  
  
> [!NOTE]
> Você pode salvar versões dimensionadas de imagens de bitmap em seu aplicativo, e o Windows carregará a imagem correta para a escala atual. Para obter mais informações, consulte o [design responsivo 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). No entanto, se você alterar a resolução do simulador de modo que o Windows selecione uma imagem diferente para ajustar à resolução, será preciso parar e reiniciar a sessão de depuração para exibir a nova imagem.  
  
## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Capture uma captura de tela de seu aplicativo para envio para a Windows Store  
 Ao enviar um aplicativo para a loja de aplicativos do Windows, você deve incluir capturas de tela do aplicativo.  
  
> [!NOTE]
> A captura de tela é salva na resolução atual do simulador. Para alterar a resolução, escolha o botão **Alterar Resolução**.  
  
- Para criar capturas de tela do aplicativo por meio do simulador, escolha o botão **Capturar tela na área de transferência**.  
  
- Para definir o local em que as capturas de tela estão localizadas, escolha o botão **configurações de captura de tela** e escolha o local no menu de atalho.  
  
     ![Menu de contexto de configurações de captura de tela](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
## <a name="BKMK_Simulate_network_connection_properties"></a> Simular propriedades de conexão de rede  
 Você pode ajudar os usuários de seu aplicativo a gerenciar o custo de conexões de rede limitadas mantendo a percepção do custo da conexão de rede ou as alterações de status do plano de dados e habilitando o aplicativo para usar essas informações para evitar a cobrança de custos adicionais para roaming ou exceder um limite especificado de transferência de dados. As APIs [Windows. Networking. Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) permitem responder a eventos [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) e [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) que assinam. Consulte [início rápido: Gerenciando restrições de custo de rede limitada](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Para depurar ou testar seu código de reconhecimento de custos de rede, o simulador pode imitar as propriedades de uma rede que são expostas por meio do objeto [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) retornado pelo [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)..  
  
 {13&gt;Para simular propriedades de rede:&lt;13}  
  
1. Na barra de ferramentas do simulador, escolha o botão **alterar propriedades da rede** .  
  
2. Na caixa de diálogo **Definir Propriedades de Rede**, selecione **Usar propriedades de rede simulada**.  
  
    {1&gt;Desmarque a caixa de seleção para remover a simulação e retornar às propriedades de rede da interface atualmente conectada.&lt;1}  
  
3. Digite um **Nome de Perfil** para a rede simulada. É recomendável usar um nome exclusivo que você pode usar para identificar a simulação na propriedade [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) do objeto [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) .  
  
4. Selecione o valor [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) para o perfil na lista **tipo de custo de rede** .  
  
5. Na lista **sinalizador de status do limite de dados** , você pode definir a propriedade [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) ou a propriedade [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)como true ou pode escolher **em limite de dados** para definir os dois valores como false.  
  
6. Na lista **estado de roaming** , defina a propriedade [roaming](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) .  
  
7. Escolha **definir propriedades** para simular as propriedades de rede disparando um evento [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) em primeiro plano e um [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) em segundo plano do tipo **NetworkStateChange**.  
  
   **Mais informações sobre como gerenciar conexões de rede**  
  
   [Início rápido: Gerenciando restrições de custo de rede limitada](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Exemplo de informações de rede](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analisar o uso de energia](../profiling/analyze-energy-use-in-store-apps.md)  
    
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Como responder a eventos do sistema com tarefas em segundo plano](https://msdn.microsoft.com/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Como disparar eventos de suspensão, retomada e segundo plano em aplicativos da Windows Store](https://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Navegar no simulador com o teclado  
 Você pode navegar na barra de ferramentas do simulador pressionando **Ctrl + Alt + seta para cima** para alternar o foco da janela simular para a barra de ferramentas do simulador. Use a **seta para cima** e a **seta para baixo** para navegar entre os botões da barra de ferramentas.  
  
 Você pode desligar o simulador pressionando **Ctrl + Alt + F4**.  
  
## <a name="see-also"></a>Veja também  
 [Executar aplicativos usando o Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
