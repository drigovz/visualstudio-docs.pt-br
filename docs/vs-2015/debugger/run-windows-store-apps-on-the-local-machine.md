---
title: Executar aplicativos da Windows Store no computador local | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196310"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Executar aplicativos da Windows Store na máquina local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se somente ao Windows] (.. /Imagem/windows_only_content.png "windows_only_content")  
  
 Para depurar, testar ou executar análise de desempenho em um aplicativo da Windows Store, você pode executar o aplicativo no mesmo computador host do Visual Studio. Se a tela do dispositivo for habilitada para toque, você poderá ativar a funcionalidade completa do aplicativo; do contrário, você estará limitado aos gestos do mouse e do teclado.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Neste tópico  
 Você aprende sobre:  
  
 [Como executar em um computador local](#BKMK_How_to_run_on_a_local_machine)  
  
 [Como alternar entre um aplicativo da Windows Store e do Visual Studio em um único monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Como executar em um computador local  
 Para executar o aplicativo no computador local, selecione **computador local** na lista suspensa ao lado do botão Iniciar Depuração na barra de ferramentas **padrão** do depurador.  
  
 ![Executar no computador local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Se você não conseguir ver a barra de ferramentas **padrão** , clique no menu **Exibir** , aponte para **barras de ferramentas**e clique em **padrão**.  
  
 A escolha que você faz na lista suspensa persiste no arquivo de propriedades do projeto e se torna o destino de execução padrão.  
  
 Você também pode definir o destino de execução diretamente no arquivo de propriedades do projeto. Clique com o botão direito do mouse no nome do projeto em **Gerenciador de soluções** e escolha **Propriedades**. Siga um destes procedimentos:  
  
- Em projetos do C# e Visual Basic, clique em **depurar** e, em seguida, selecione **computador local** na lista suspensa **dispositivo de destino** .  
  
     ![C&#35; e Visual Basic página de propriedades do projeto](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- Em projetos C++ e JavaScript, expanda o nó **Propriedades de configuração** , clique em **depuração**e selecione **depurador local** na lista **depurador a ser iniciado** .  
  
     ![Página de propriedades do projeto C&#43;&#43; e JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Como alternar entre um aplicativo da Windows Store e o Visual Studio em um único monitor  
 **Para alternar de uma instância em execução de um aplicativo da Windows Store ao Visual Studio**  
  
 Quando você executa um aplicativo da Windows Store em um computador local e usa apenas um único monitor, você pode querer alternar para o Visual Studio enquanto deixa o aplicativo em execução. Por exemplo, o aplicativo pode estar em um estado que não pode ser alcançado por um ponto de interrupção, como esperar por um evento ou estar preso em um loop extenso ou sem fim. Para retornar ao Visual Studio, pressione ALT+TAB.
