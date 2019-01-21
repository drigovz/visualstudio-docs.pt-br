---
title: Instalar a versão prévia do Visual Studio 2019 para Mac
description: Instruções sobre como instalar a versão prévia do Visual Studio 2019 para Mac e os componentes adicionais necessários para o desenvolvimento em várias plataformas.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: acd8f3bc4f5fefa0a0c8b273856579067fb33c6a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315894"
---
# <a name="install-visual-studio-2019-for-mac-preview"></a>Instalar a versão prévia do Visual Studio 2019 para Mac

> [!NOTE]
> A versão prévia do Visual Studio 2019 para Mac está disponível para instalação lado a lado com a versão estável mais recente do Visual Studio para Mac. Durante a instalação você precisará atualizar seu Visual Studio existente, caso não seja a versão estável mais recente.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Requisitos para a versão prévia do Visual Studio 2019 para Mac

- Um Mac com macOS High Sierra 10.13 ou superior.

Para criar aplicativos Xamarin para iOS ou macOS, você também precisará de:

- Xcode 10.0 ou posterior. A versão estável mais recente geralmente é recomendada.
- Uma ID da Apple. Se ainda não tiver uma ID da Apple, crie uma nova em https://appleid.apple.com. Será necessário ter uma ID da Apple para instalar e entrar no Xcode.

## <a name="installing-the-preview"></a>Instalando a versão prévia

1. Baixe o instalador da versão prévia da [página da versão prévia do Visual Studio para Mac](https://aka.ms/vs4mac-preview).
2. Depois que o download for concluído, clique no **VisualStudioforMacPreviewInstaller.dmg** para montar o instalador e, em seguida, execute-o clicando duas vezes no logotipo de seta:

    [![Clique na seta grande para iniciar a instalação](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Poderá ser apresentado a você um aviso de que o aplicativo está sendo baixado da Internet. Clique em **Abrir**.
4. Aguarde enquanto o instalador verifica seu sistema:

    [![O instalador verifica o sistema em busca de componentes instalados](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Um alerta será exibido solicitando que você reconheça os termos de licença e privacidade. Siga os links para lê-los e, em seguida, pressione **Continuar** se você concordar com eles:

    [![Siga os links para a privacidade e termos e, em seguida, continue se você concordar com eles](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. A lista de cargas de trabalho disponíveis é exibida. Selecione aquelas que você deseja usar:

    [![Escolha quais recursos opcionais de carga de trabalho você deseja instalar](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Caso seu Visual Studio para Mac 2017 atual seja anterior à versão 7.7, será solicitado que você aprove uma atualização para a versão estável mais recente (necessário para dar suporte à instalação lado a lado). Pressione **Continuar** para aprovar a atualização:

    ![A atualização da versão estável para 7.7 é necessária](media/install-preview-older-upgrade.png)

7. Após você ter feito suas seleções, pressione o botão **Instalar**.
8. O instalador exibirá o andamento conforme o download acontece e instalará o Visual Studio para Mac e as cargas de trabalho selecionadas. Talvez seja solicitado que você insira sua senha para conceder os privilégios necessários para a instalação.
9. Use o **Visual Studio (Preview)** sempre que quiser testar a versão prévia ou então volte para a versão estável mais recente do Visual Studio para o seu trabalho de produção. Os dois ícones são mostrados aqui:

    ![Diferenças entre os ícones de versão prévia e estável](media/install-preview-icons-sml.png)

Se você tiver problemas de rede durante a instalação em um ambiente corporativo, examine as instruções em [instalação por trás de um firewall ou proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Saiba mais sobre as novidades nas [notas sobre a versão](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

> [!NOTE]
> Se você optou por não instalar uma plataforma ou ferramenta durante a instalação original (desmarcando-a na etapa 6), deve executar o instalador novamente se quiser adicionar os componentes mais tarde.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalar o Visual Studio para Mac por trás de um firewall ou servidor proxy

Para instalar o Visual Studio para Mac por trás de um firewall, determinados pontos de extremidade devem estar acessíveis para permitir o download das ferramentas necessárias e as atualizações do software.

Configure a rede para permitir o acesso aos seguintes locais:

- [Pontos de extremidade do Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Próximas etapas

A instalação do Visual Studio para Mac permite que você comece a escrever código para seus aplicativos. Os guias a seguir são fornecidos para orientar você durante as próximas etapas da criação e implantação de seus projetos.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Provisionamento de dispositivo](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (para executar o aplicativo no dispositivo).

### <a name="android"></a>Android

1. [Usando o Gerenciador de SDK do Xamarin Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulador do SDK do Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Configurar o dispositivo para desenvolvimento](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplicativos .NET Core, aplicativos Web do ASP.NET Core, desenvolvimento de jogos em Unity

Para outras cargas de trabalho, confira a página [Cargas de trabalho](/visualstudio/mac/workloads).

## <a name="see-also"></a>Consulte também

- [Instalar o Visual Studio 2017 (no Windows)](/visualstudio/install/install-visual-studio)
