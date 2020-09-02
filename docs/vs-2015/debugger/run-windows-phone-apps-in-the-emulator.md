---
title: Executar Windows Phone aplicativos no emulador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683533"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Executar aplicativos do Windows Phone no emulador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O emulador de Windows Phone fornece um ambiente virtualizado no qual você pode depurar e testar Windows Phone aplicativos em seu computador sem um dispositivo físico. Você pode simular eventos comuns de toque e rotação e escolher o tamanho da tela física e a resolução que deseja emular. Você também pode testar muitas funcionalidades normalmente usadas, como local, rede, notificações, sensores, acelerômetro e cartão SD opcional.  
  
 Para obter mais informações sobre os recursos que você pode testar no emulador, consulte [testar os recursos do aplicativo no emulador de Windows Phone](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Junto com o Visual Studio, o emulador fornece um ambiente completo em que você pode criar, desenvolver, depurar e testar aplicativos do Windows Phone.  
  
## <a name="run-a-windows-phone-app-in-the-emulator"></a><a name="BKMK_run"></a> Executar um aplicativo Windows Phone no emulador  
 Enquanto você desenvolve um aplicativo do Windows Phone, pode usar o Emulador do Windows Phone para implantar e testar seu aplicativo rapidamente. Recomendamos que você teste seu aplicativo em um dispositivo Windows Phone real, mas antes de publicar seu aplicativo na Windows Phone Store. Isso permite que você tenha experiências com seu aplicativo da mesma forma que os usuários terão.  
  
 Quando você executa um aplicativo do Windows Phone pela primeira vez no Emulador do Windows Phone, podem ocorrer os seguintes eventos:  
  
1. O emulador é iniciado.  
  
2. O emulador carrega o sistema operacional do Windows Phone.  
  
3. O emulador exibe a tela inicial do Windows Phone.  
  
4. Seu aplicativo é implantado no emulador.  
  
5. Seu aplicativo é executado no emulador.  
  
   Se o emulador selecionado já estiver em execução, seu aplicativo é implantado e iniciado no emulador em execução. Apenas uma instância de cada emulador pode executar de cada vez.  
  
> [!TIP]
> Quando você testar seu aplicativo no emulador, deixe o emulador aberto entre as sessões de depuração, assim poderá reexecutar seu aplicativo rapidamente.  
  
### <a name="run-an-app-from-visual-studio"></a><a name="BKMK_vs"></a> Executar um aplicativo do Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Para implantar e executar o aplicativo do Visual Studio  
  
1. No Visual Studio, abra um projeto do Windows Phone.  
  
2. Na barra de ferramentas **padrão** , selecione uma das opções de emulador.  
  
     ![Lista de imagens de emulador de Windows Phone](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Para implantar e executar seu aplicativo com depuração, no menu **depurar** , clique em **Iniciar Depuração**ou pressione F5.  
  
     Para implantar e executar seu aplicativo sem depuração, no menu **depurar** , clique em **Iniciar sem depuração**ou pressione CTRL + F5.  
  
     Seu aplicativo é implantado e iniciado.  
  
     Para implantar seu aplicativo sem executá-lo, no menu **Compilar** , clique em **implantar solução**.  
  
##### <a name="to-stop-a-running-app"></a>Para interromper a execução de um aplicativo  
  
- Para interromper um aplicativo em execução, faça o seguinte:  
  
  - No Visual Studio, no menu **depurar** , clique em **parar depuração**ou pressione Shift + F5.  
  
  - No emulador, pressione o botão **voltar** para sair do aplicativo. Se a página ativa do aplicativo não for a página inicial do aplicativo, talvez você precise pressionar o botão **voltar** mais de uma vez.  
  
    O aplicativo sai e a tela Iniciar abre. Isso encerra a sessão de depuração atual.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Para reiniciar um aplicativo sem depuração  
  
1. No emulador, na tela Iniciar, passe o dedo para a esquerda para exibir a lista de aplicativos.  
  
2. Na lista de aplicativos, toque no ícone do aplicativo. O aplicativo reinicia sem depuração.  
  
##### <a name="to-deactivate-a-running-app"></a>Para desativar um aplicativo em execução  
  
1. Antes de executar seu aplicativo, no Visual Studio, clique com o botão direito do mouse no projeto em Gerenciador de Soluções e, em seguida, selecione **Propriedades** para abrir o **Designer de projeto**.  
  
2. No **Designer de projeto**, na página de **depuração** , deixe a caixa de seleção **desativação ao desativá** -la durante a depuração desmarcada se você quiser que o aplicativo entre em um estado inativo quando desativado. Marque a caixa de seleção se você deseja que o aplicativo fique inativo quando for desativado.  
  
3. No menu **depurar** , clique em **Iniciar Depuração**ou pressione F5 para executar o aplicativo.  
  
4. No emulador, pressione o botão **Iniciar** . A tela Iniciar aparece e o aplicativo é desativado. O aplicativo entra em um estado inativo ou é marcado para exclusão, dependendo da configuração da caixa de seleção **desativação ao depurar durante a depuração** .  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Para reativar um dispositivo dormente ou inativo  
  
- No emulador, pressione o botão **voltar** para retornar ao aplicativo. Se você navegou para outras páginas ou abriu outro aplicativo, pode ser necessário pressionar o botão **voltar** mais de uma vez para reativar o aplicativo.  
  
     A sessão de depuração é retomada. Se o depurador se soltou de seu aplicativo, pode ser necessário pressionar F5 pra retomar a sessão de depuração.  
  
### <a name="run-an-app-with-the-application-deployment-tool"></a><a name="BKMK_depltool"></a> Executar um aplicativo com a ferramenta de implantação de aplicativos  
 Você também pode usar a**AppDeploy.exe**(ferramenta de implantação de aplicativo) Windows Phone para executar seu aplicativo no emulador. Essa ferramenta é um aplicativo independente, que é implantado quando você instala as ferramentas de desenvolvimento do Windows Phone.  
  
 Para obter mais informações, consulte [implantar Windows Phone aplicativos 8,1 com a ferramenta de implantação de aplicativos](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="configure-the-windows-phone-emulator-with-the-emulator-toolbar"></a><a name="BKMK_toolbar"></a> Configurar o emulador de Windows Phone com a barra de ferramentas do emulador  
 Esta tabela mostra os botões de configuração disponíveis na barra de ferramentas do emulador.  
  
|Botões da barra de ferramentas|Opções de configuração|  
|---------------------|---------------------------|  
|![Opções de entrada na barra de ferramentas do emulador Windows Phone](../debugger/media/wp-emulator.png "WP_Emulator_")|**Configurar entrada de um único ponto ou vários pontos**<br /><br /> Quando você habilita a entrada de vários pontos, pode clicar com o botão direito do mouse para mover os pontos de toque sem tocar na tela. E você pode clicar com o botão esquerdo para mover os dois pontos de toque simultaneamente.|  
|![Orientação na barra de ferramentas do emulador Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Configurar a orientação do emulador**<br /><br /> Você pode alterar a orientação no Emulador do Windows Phone para uma das três orientações: retrato, paisagem à esquerda ou paisagem à direita. O tamanho do emulador não muda quando você muda a orientação.<br /><br /> Para alterar a orientação, clique no botão **girar à esquerda** ou no botão girar para a **direita** .|  
|![Opções de tamanho na barra de ferramentas do emulador Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Configurar o tamanho do emulador**<br /><br /> Você pode mudar o tamanho do emulador na tela do computador host. O DPI (pontos por polegada) para o emulador é baseado no DPI do monitor host, independentemente do valor de zoom.<br /><br /> -Para ajustar o emulador à tela, clique no botão **ajustar à tela** .<br />-Para alterar a configuração de zoom, clique no botão **zoom** . A caixa de diálogo **zoom** é aberta. Na caixa de diálogo **zoom** , insira um valor de Zoom entre 33 e 100.|  
  
## <a name="use-the-simulated-hardware-buttons-on-the-emulator"></a><a name="BKMK_buttons"></a> Usar os botões de hardware simulados no emulador  
 Simule o uso dos botões de hardware de um telefone usando os botões de hardware simulados no lado direito da tela do emulador.  
  
- Clique no botão **ligar/desligar** para simular a desativação da exibição. Clique e segure para simular o desligamento do telefone.  
  
- Clique no botão **volume acima** ou **volume abaixo** para simular a alteração do volume do alto-falante do telefone para chamadas telefônicas e notificações.  
  
- O botão **câmera** inicia o aplicativo de câmera. Você pode simular tirar uma foto ou um vídeo usando os controles no aplicativo de câmera.  
  
  A captura de tela a seguir mostra os botões de hardware simulados.  
  
1. A imagem à esquerda exibe a tela Iniciar no emulador.  
  
2. A imagem intermediária exibe o emulador depois de tocar no botão de **energia** para desativar a exibição.  
  
3. A imagem correta exibe a tela do emulador depois de tocar no botão **volume up** para aumentar o volume.  
  
   ![Botões no emulador de Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="use-the-computer-keyboard-with-the-emulator"></a><a name="BKMK_tasks_kbd"></a> Usar o teclado do computador com o emulador  
 O emulador suporta mapeamento do teclado de hardware em seu computador de desenvolvimento para teclado em um Windows Phone. O comportamento das teclas é igual ao de um dispositivo Windows Phone.  
  
 Por padrão, o teclado de hardware não fica habilitado. A implementação é equivalente a um teclado deslizante que deve ser implantado antes de você poder usá-lo. Antes de você habilitar o teclado de hardware, o emulador só aceita entrada de teclas das teclas de controle.  
  
 O emulador não suporta caracteres especiais no teclado de uma versão localizada de um computador de desenvolvimento do Windows. Para inserir caracteres especiais presentes em teclados localizados, use o SIP (Software Input Panel).  
  
 Para usar o teclado do computador no emulador, pressione a tecla PAGE UP ou a tecla PAUSE/BREAK (emulador do Windows 8/8.1) ou F4 (emulador do Windows 10).  
  
 Para parar de usar o teclado do computador no emulador, pressione a tecla PAGE DOWN ou a tecla PAUSE/BREAK (emulador do Windows 8/8.1) ou F4 (emulador do Windows 10).  
  
 A tabela a seguir lista as teclas em um teclado de hardware que você pode usar para emular os botões e outros controles em um Windows Phone.  
  
|Tecla de hardware do computador|Botão de hardware do Windows Phone|Observações|  
|---------------------------|-----------------------------------|-----------|  
|F1|VOLTAR|Pressionar longamente funciona como esperado.|  
|F2|START|Pressionar longamente funciona como esperado.|  
|F3|SEARCH||  
|F4|No emulador do Windows 10, alterna entre usar o teclado do computador local e não usar o teclado do computador local.|Não aplicável no emulador do Windows 8/8.1.|  
|F5|Não aplicável.||  
|F6|METADE DA CÂMERA|Um botão de câmera dedicado, que é pressionado apenas um pouco.|  
|F7|CÂMERA INTEIRA|Um botão de câmera dedicado.|  
|F8|Não aplicável.||  
|F9|AUMENTAR VOLUME||  
|F10|DIMINUIR VOLUME||  
|F11|Não aplicável.||  
|F12|POWER|Pressione a tecla F12 duas vezes para habilitar a tela de bloqueio.<br /><br /> Pressionar longamente funciona como esperado.|  
|ESC|VOLTAR|Pressionar longamente funciona como esperado.|  
|PAUSE/BREAK|Ativar/desativar teclado (somente emulador do Windows 8/8.1).|Não aplicável ao emulador do Windows 10.|  
|PAGE UP|Habilita o teclado de hardware (somente emulador do Windows 8/8.1).|Não aplicável ao emulador do Windows 10.|  
|PAGE DOWN|Desabilita o teclado de hardware (somente emulador do Windows 8/8.1).|Não aplicável ao emulador do Windows 10.|  
  
## <a name="save-and-load-custom-checkpoints"></a><a name="BKMK_checkpoints"></a> Salvar e carregar pontos de verificação personalizados  
 Salve um instantâneo do estado do emulador usando a guia **pontos de verificação** das **ferramentas adicionais**do emulador. Essa funcionalidade é útil quando você testa seu aplicativo frequentemente com os mesmos dados e configurações.  
  
 Por exemplo, se seu aplicativo requer vários contatos, você pode criar os registros de contato uma vez e salvar um instantâneo do emulador. Do contrário, você tem de recriar o registro de contato toda vez que iniciar o emulador.  
  
- Clique em **novo ponto de verificação** para capturar um novo instantâneo do estado do emulador com os dados e as configurações necessárias para testar seu aplicativo novamente mais tarde. O novo ponto de verificação é adicionado à lista **pontos de verificação** .  
  
   Você não pode capturar um ponto de verificação enquanto o depurador estiver anexado ao emulador.  
  
- Selecione um ponto de verificação na lista **pontos de verificação** para exibir informações sobre o ponto de verificação.  
  
- Selecione o botão de opção na coluna **padrão** para fazer um ponto de verificação salvo no ponto de verificação padrão do emulador ativo.  
  
- Clique em **restaurar** para reiniciar o sistema operacional Windows Phone no emulador e carregar o instantâneo selecionado.  
  
- Clique em **excluir** para excluir um instantâneo que você não precisa mais.  
  
  A imagem do emulador original sempre aparece como o primeiro item na lista **pontos de verificação** e não pode ser alterada ou excluída. No entanto, você pode selecionar um instantâneo diferente como imagem padrão do emulador.  
  
  ![Guia pontos de verificação do emulador de Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="capture-screenshots-in-the-emulator"></a><a name="BKMK_tasks_shot"></a> Capturar capturas de tela no emulador  
 Você pode criar capturas de tela de seus aplicativos do Windows Phone usando a ferramenta de captura de tela a partir da janela Ferramentas adicionais. A ferramenta cria arquivos PNG que correspondem à resolução do emulador em execução.  
  
 ![Capturas de tela do emulador de Windows Phone](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Para criar uma captura de tela do aplicativo usando a ferramenta de captura de tela interna do emulador  
  
1. Para otimizar a qualidade de suas capturas de tela, defina o nível de zoom do emulador para 100%. Quanto mais alto você definir o nível de zoom, melhor será a qualidade da captura de tela.  
  
2. Inicie seu aplicativo no emulador.  
  
3. Na barra de ferramentas do emulador, clique no botão expandir para abrir a janela **ferramentas adicionais** .  
  
4. Clique na guia **captura de tela** .  
  
5. Quando seu aplicativo estiver pronto, clique no botão **capturar** .  
  
    A captura de tela aparece no workspace.  
  
6. Clique no botão **salvar** para abrir a caixa de diálogo **salvar como** .  
  
7. Escolha o local e o **nome do arquivo** desejado e clique em **salvar**.  
  
8. Como opção, navegue para outras páginas em seu aplicativo para capturar telas adicionais.  
  
9. Inicie o emulador com uma resolução de tela diferente para capturar as mesmas telas com uma resolução diferente. Se você executou seu aplicativo ao depurar, é necessário parar a depuração antes de poder executá-lo novamente em outro emulador.  
  
   Desabilite os contadores de taxa de quadros na tela do emulador antes de capturar telas que serão enviadas à Windows Phone Store.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Para desabilitar os contadores de taxa de quadros no emulador antes de capturar telas  
  
- Especifique uma criação de versão no Visual Studio. Depois de especificar uma compilação de versão, inicie o aplicativo selecionando o link **implantar _[nome do aplicativo]_ ** no menu **Compilar** .  
  
- Como alternativa, você pode comentar na linha de código do arquivo app.xaml.cs ou app.xaml.vb que define o valor de `EnableFrameRateCounter` para `true`.
