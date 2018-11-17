---
title: Implantar aplicativos UWP do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 974236f005219caa217f8b1b495eb807ab2f6ee0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726307"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Implantar aplicativos UWP usando o Visual Studio

A funcionalidade de implantação do Visual Studio cria e registra aplicativos UWP que são criados com o Visual Studio em um dispositivo de destino. Exatamente como o aplicativo é registrado depende de o dispositivo de destino ser local ou remoto:

- Quando o destino é o computador local com o Visual Studio, ele registra o aplicativo de sua pasta de build.

- Quando o destino é um dispositivo remoto, o Visual Studio copia os arquivos necessários ao computador remoto e registra o aplicativo nesse dispositivo.

Implantação é automática quando você depura seu aplicativo do Visual Studio usando o **iniciar depuração** opção (teclado: F5) ou o **Start Without Debugging** opção (teclado: CTRL + F5). Você também pode implantar seu aplicativo manualmente. A implantação manual é útil nos seguintes cenários:

- Teste ad-hoc em um computador local ou remoto.

- Implantação de um aplicativo que iniciará outro aplicativo que você quer depurar.

- Implantação de um aplicativo que será depurado quando é iniciado por outro aplicativo ou método.

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Como implantar um aplicativo UWP
 Implantar manualmente um aplicativo é simples:

1.  Se você está implantando para um dispositivo remoto, especifique o nome ou o endereço IP do dispositivo na página de propriedade do projeto de inicialização do aplicativo. (As etapas para fazer isso são listadas a seguir neste tópico.)

2.  Na barra de ferramentas do depurador Visual Studio, escolha o destino de implantação na lista suspensa ao lado de **iniciar depuração** botão.

     ![Executar no computador Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3.  Sobre o **construir** menu, escolha **implantar**

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Como especificar um dispositivo remoto

**Pré-requisitos**

Em um dispositivo remoto do Windows 10, você deve habilitar [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development). Em dispositivos Windows 10 que executam a atualização do criador ou posterior, as ferramentas remotas são instaladas automaticamente quando você implanta seu aplicativo. Para obter mais informações, consulte [depurar pacote de aplicativo instalado](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Em versões de atualização do pre-criador do Windows 10, as ferramentas remotas para Visual Studio deve ser instaladas no dispositivo remoto e o depurador remoto deve estar em execução.

A implantação usa o canal de rede do depurador remoto para enviar os arquivos do aplicativo ao dispositivo remoto.

#### <a name="to-specify-a-remote-device"></a>Para especificar um dispositivo remoto

1. Na página de propriedade de depuração do projeto de inicialização, especifique o nome ou o endereço IP de um destino de implantação remoto.

2. Para abrir a página de propriedades de depuração, escolha o projeto no Gerenciador de soluções e, em seguida, escolha **propriedades** no menu de atalho.

3. Em seguida, escolha o **depurar** nó na janela de páginas de propriedade.

4. Para **dispositivo de destino**, selecione **máquina remota**.

5. Sob **computador remoto**, clique em **localizar**.

6. Você pode digitar o nome ou endereço IP do dispositivo remoto, ou você pode escolher o dispositivo a partir de **Conexão remota** caixa de diálogo.

    ![Marque a caixa de diálogo Conexão de depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    O **Conexão remota** caixa de diálogo exibe os dispositivos na sub-rede local e em qualquer dispositivo que está conectado diretamente ao computador do Visual Studio por um cabo Ethernet.

   **Especificar o dispositivo remoto em uma página de projeto do Visual C++ ou JavaScript**

   ![C&#43; &#43; propriedades para depuração remota do projeto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Escolher **depurador remoto** da **depurador a iniciar** lista.

8. Insira o nome de rede do dispositivo remoto na **nome da máquina** caixa. Ou então, você pode escolher a seta para baixo na caixa para selecionar o dispositivo da caixa de diálogo Selecionar Conexão de Depurador Remoto.

   **Especificar o dispositivo remoto em uma página de projeto do Visual c# e Visual Basic**

   ![Gerenciado propriedades do projeto para depuração remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Escolher **computador remoto** da **dispositivo de destino** lista.

10. Insira o nome de rede do dispositivo remoto na **computador remoto** caixa ou clique em **localizar** para escolher o dispositivo dos **Selecionar Conexão de depurador remoto** caixa de diálogo.

##  <a name="BKMK_Deployment_options"></a> Opções de implantação

Você pode definir as opções de implantação a seguir na página de propriedade de depuração do projeto de inicialização.

**Permitir Loopback de rede**

Por motivos de segurança, um UWP ou [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativo instalado da maneira padrão não tem permissão para fazer chamadas de rede para o dispositivo está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], você deve testá-lo sem a isenção.

Para remover a isenção de loopback de rede do aplicativo:

- Sobre o C# e Visual Basic Depurar página de propriedades, desmarque a **permitir Loopback de rede** caixa de seleção.

- Na página de propriedade de JavaScript e depuração, defina as **permitir Loopback de rede** valor para **não**.

**Não iniciar, mas depurar meu código quando ele é iniciado (C# e Visual Basic) / Iniciar aplicativo (JavaScript e C++)**

Para configurar a implantação para iniciar automaticamente uma sessão de depuração quando o aplicativo é iniciado:

- Sobre o C# e a página de propriedades de depuração do Visual Basic, verifique o **não iniciar, mas depurar meu código quando ele é iniciado** caixa de seleção.

- Na página de propriedade de JavaScript e depuração, defina as **aplicativo&lt;3}.&lt;1** valor para **Sim**.

## <a name="see-also"></a>Consulte também

- [Opções de implantação remota avançadas](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Depurar pacote de aplicativo instalado](../debugger/debug-installed-app-package.md)
- [Executar aplicativos usando o Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
