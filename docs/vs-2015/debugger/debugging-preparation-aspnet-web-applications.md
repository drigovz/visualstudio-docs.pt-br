---
title: 'Preparação da depuração: aplicativos Web ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691458"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Preparação de depuração: aplicativos Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] modelo de site cria um aplicativo de formulário da Web. Quando você cria um site usando esse modelo, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cria as configurações padrão para depuração. Na caixa de diálogo **Propriedades do projeto** , você pode especificar se deseja que a página da Web seja uma página de inicialização. Quando você inicia a depuração de um [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] site com essas configurações padrão, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] inicia o Internet Explorer e anexa o depurador ao [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processo de trabalho (aspnet_wp.exe ou w3wp.exe). Para obter mais informações, veja [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Para criar um aplicativo de Web Forms  
  
1. No menu **arquivo** , escolha **novo site**.  
  
2. Na caixa de diálogo **novo site** , selecione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **site da Web**.  
  
3. Clique em **OK**.  
  
### <a name="to-debug-your-web-form"></a>Para depurar seu Web form  
  
1. Defina um ou mais pontos de interrupção em suas funções e manipuladores de eventos.  
  
     Para obter mais informações, consulte [pontos de interrupção e tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Quando um ponto de interrupção é atingido, insira o código na função. Observe a execução do código até isolar o problema.  
  
     Para obter mais informações, [consulte depuração](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) e [depuração de aplicativos e scripts da Web](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Alterar Configurações padrão  
 Se você quiser alterar a depuração padrão e liberar as configurações criadas pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], poderá fazer isso. Para obter mais informações, consulte [como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Para alterar a configuração de depuração padrão  
  
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no site da Web e selecione **páginas de propriedades** para abrir a caixa de diálogo **páginas de propriedades** .  
  
2. Clique em **Iniciar opções**.  
  
3. Defina a **ação iniciar** para a página da Web que deve ser exibida primeiro.  
  
4. Em **depuradores**, verifique se a **depuração ASP.net** está selecionada.  
  
     Para obter mais informações, consulte [configurações de páginas de propriedades para projetos Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Configurações e preparação do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)
