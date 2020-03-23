---
ms.openlocfilehash: 0fc18fab56f5b46ef097cdf699e4f0569dc190c9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143550"
---
A Implantação da Web 3.6 para Servidores de Hospedagem fornece recursos adicionais de configuração que permitem a criação do arquivo de configurações da publicação por meio da interface do usuário.

1. Se você tiver o Web Deploy 3.6 já instalado no Windows Server, desinstale-o usando programas **de painel** > de controle**desinstale****Programs** > um programa .

2. Em seguida, instale Implantação da Web 3.6 para Servidores de Hospedagem no Windows Server.

    Para instalar a Implantação da Web para Servidores de Hospedagem, use o [WebPI (Web Platform Installer)](https://www.microsoft.com/web/downloads/platform.aspx). (Para localizar o link do Web Platform Installer do IIS, selecione **IIS** no painel esquerdo do Gerenciador do Servidor. Clique com o botão direito do mouse e selecione **Gerenciador do IIS (Serviços de Informações da Internet)**).

    No Web Platform Installer, você encontra a **Implantação da Web para Servidores de Hospedagem** na guia Aplicativos.

3. Se você ainda não instalou as **Ferramentas e Scripts de Gerenciamento do IIS**, instale-as agora.

    Vá para **Selecionar funções do** > servidor Ferramentas**de gerenciamento**do Servidor Web **(IIS)** > e, em seguida, selecione a função **Scripts e Ferramentas de Gerenciamento de IIS,** clique em **Next**e, em seguida, instale a função.

    ![Instalar Scripts de gerenciamento e ferramentas do IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Os scripts e as ferramentas são necessários para permitir a geração do arquivo de configurações da publicação.

4. (Opcional) Verifique se a Implantação da Web está em execução corretamente abrindo **Painel de Controle > Sistema e Segurança > Ferramentas Administrativas > Serviços** e verifique se o **Serviço do Agente de Implantação da Web** está em execução (o nome do serviço é diferente em versões mais antigas).

    Se o serviço de agente não estiver em execução, inicie-o. Se não estiver presente, acesse **Painel de Controle > Programas > Desinstalar um programa**, localize **Implantação da Web da Microsoft \<versão>**. Escolha **Alterar** a instalação e certifique-se de escolher **Será instalado na unidade de disco rígido local** para os componentes de Implantação da Web. Conclua as etapas de instalação de alteração.