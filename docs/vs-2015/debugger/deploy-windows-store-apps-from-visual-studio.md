---
title: Implantar aplicativos da Windows Store
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177460"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Implantar aplicativos da Windows Store pelo Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se somente ao Windows] (.. /Imagem/windows_only_content.png "windows_only_content")

 A funcionalidade de implantação do Visual Studio compila e registra aplicativos na Windows Store que são criados com o Visual Studio em um dispositivo de destino. Exatamente como o aplicativo é registrado depende de o dispositivo de destino ser local ou remoto:

- Quando o destino é o computador local com o Visual Studio, ele registra o aplicativo de sua pasta de build.

- Quando o destino é um dispositivo remoto, o Visual Studio copia os arquivos necessários ao computador remoto e registra o aplicativo nesse dispositivo.

  A implantação é automática quando você depura seu aplicativo do Visual Studio usando a opção **Iniciar Depuração** (teclado: F5) ou a opção **Iniciar sem depuração** (teclado: CTRL + F5). Você também pode implantar seu aplicativo manualmente. A implantação manual é útil nos seguintes cenários:

- Teste ad-hoc em um computador local ou remoto.

- Implantação de um aplicativo que iniciará outro aplicativo que você quer depurar.

- Implantação de um aplicativo que será depurado quando é iniciado por outro aplicativo ou método.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Neste tópico
 Neste tópico, você pode aprender:

 [Como implantar um aplicativo da Windows Store](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Como especificar um dispositivo remoto](#BKMK_How_to_specify_a_remote_device)

 [Opções de implantação](#BKMK_Deployment_options)

## <a name="how-to-deploy-a-windows-store-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Como implantar um aplicativo da Windows Store
 Implantar manualmente um aplicativo é simples:

1. Se você está implantando para um dispositivo remoto, especifique o nome ou o endereço IP do dispositivo na página de propriedade do projeto de inicialização do aplicativo. (As etapas para fazer isso são listadas a seguir neste tópico.)

2. Na barra de ferramentas Visual Studio do depurador, escolha o destino da implantação na lista suspensa ao lado do botão **Iniciar Depuração**.

     ![Executar no computador local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. No menu **Compilar**, escolha **Implantar**

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Como especificar um dispositivo remoto
 **Pré-requisitos**

 Para implantar um aplicativo em um dispositivo remoto:

- Uma licença de desenvolvedor deve estar instalada no dispositivo remoto.

- As Ferramentas Remotas do Visual Studio devem estar instaladas no dispositivo remoto e o Monitor de Depuração Remota deve estar em execução.

     A implantação usa o canal de rede do depurador remoto para enviar os arquivos do aplicativo ao dispositivo remoto.

#### <a name="to-specify-a-remote-device"></a>Para especificar um dispositivo remoto

1. Na página de propriedade de depuração do projeto de inicialização, especifique o nome ou o endereço IP de um destino de implantação remoto.

2. Para abrir a página de propriedades de depuração, escolha o projeto no Gerenciador de Soluções e **Propriedades** no menu de atalho.

3. Em seguida, escolha o nó **Depurar** na janela de páginas de propriedades.

4. Você pode digitar o nome ou o endereço IP do dispositivo remoto, ou pode escolher o dispositivo na caixa de diálogo **selecionar conexão do depurador remoto** .

    ![Caixa de diálogo Selecionar conexão do depurador remoto](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    A caixa de diálogo **selecionar conexão do depurador remoto** exibe os dispositivos na sub-rede da rede local e qualquer dispositivo conectado diretamente ao computador do Visual Studio por um cabo Ethernet.

   **Especificando o dispositivo remoto na página de projetos em JavaScript ou Visual C++**

   ![C&#43;&#43; Propriedades do projeto para depuração remota](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Escolha **Depurador Remoto** na lista **Depurador a ser iniciado**.

6. Insira o nome de rede do dispositivo remoto na caixa **Nome do Computador**. Ou então, você pode escolher a seta para baixo na caixa para selecionar o dispositivo da caixa de diálogo Selecionar Conexão de Depurador Remoto.

   **Especificando o dispositivo remoto em uma página de projetos em Visual C# e Visual Basic**

   ![Propriedades do projeto gerenciado para depuração remota](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Escolha **Computador Remoto** na lista **Dispositivo de Destino**.

8. Insira o nome de rede do dispositivo remoto na caixa **Computador Remoto** ou clique em **Localizar** para escolher o dispositivo na caixa de diálogo **Selecionar conexão de depurador remoto**.

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Opções de implantação
 Você pode definir as opções de implantação a seguir na página de propriedade de depuração do projeto de inicialização.

 **Permitir loopback de rede** Por motivos de segurança, um [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplicativo que é instalado da maneira padrão não é permitido para fazer chamadas de rede para o dispositivo no qual ele está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)], você deve testá-lo sem a isenção.

 Para remover a isenção de loopback de rede do aplicativo:

- Na página de propriedades depurar C# e VB, desmarque a caixa de seleção **permitir loopback de rede** .

- Na página de propriedades JavaScript e depuração, defina o valor de **Permitir loopback de rede** como **Não**.

  **Não iniciar, mas depurar meu código quando ele iniciar (C# e VB)/iniciar aplicativo (JavaScript e C++)** Para configurar a implantação para iniciar automaticamente uma sessão de depuração quando o aplicativo é iniciado:

- Na página de propriedades depurar C# e VB, marque a caixa de seleção não **Iniciar, mas depurar meu código ao iniciar** .

- Na página de propriedades JavaScript e depuração, defina o valor de **Iniciar Aplicativo** como **Sim**.

## <a name="see-also"></a>Consulte Também
 [Executar aplicativos do Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
