---
ms.openlocfilehash: 1e6c6714720d652fff266e3e852d01982c98e34a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173859"
---
A Implantação da Web 3.6 para Servidores de Hospedagem fornece recursos adicionais de configuração que permitem a criação do arquivo de configurações da publicação por meio da interface do usuário.

1. Se você tiver implantação da Web 3,6 já instalado no Windows Server, desinstale-o usando programas do **painel**  >  **Programs**  >  **de controle desinstalar um programa**.

2. Em seguida, instale Implantação da Web 3.6 para Servidores de Hospedagem no Windows Server.

    Para instalar a Implantação da Web para Servidores de Hospedagem, use o WebPI (Web Platform Installer). (Para localizar o link do Web Platform Installer do IIS, selecione **IIS** no painel esquerdo do Gerenciador do Servidor. No painel servidor, clique com o botão direito do mouse no servidor e selecione **Gerenciador de serviços de informações da Internet (IIS)**. Em seguida, use o link **obter novos componentes da Web Platform** na janela **ações** .) Você também pode obter o Web Platform Installer (WebPI) de [downloads](https://www.microsoft.com/web/downloads/platform.aspx).

    Na Web Platform Installer, você encontrará **Implantação da Web 3,6 para servidores de hospedagem** na guia aplicativos.

3. Se você ainda não instalou as **Ferramentas e Scripts de Gerenciamento do IIS**, instale-as agora.

    Vá para **selecionar funções de servidor**  >  ferramentas de gerenciamento**servidor Web (IIS)**  >  **Management Tools**e, em seguida, selecione a função **scripts e ferramentas de gerenciamento do IIS** , clique em **Avançar**e, em seguida, instale a função.

    ![Instalar Scripts de gerenciamento e ferramentas do IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Os scripts e as ferramentas são necessários para permitir a geração do arquivo de configurações da publicação.

4. (Opcional) Verifique se a Implantação da Web está em execução corretamente abrindo **Painel de Controle > Sistema e Segurança > Ferramentas Administrativas > Serviços** e verifique se o **Serviço do Agente de Implantação da Web** está em execução (o nome do serviço é diferente em versões mais antigas).

    Se o serviço de agente não estiver em execução, inicie-o. Se não estiver presente, acesse **Painel de Controle > Programas > Desinstalar um programa**, localize **Implantação da Web da Microsoft \<version>**. Escolha **Alterar** a instalação e certifique-se de escolher **Será instalado na unidade de disco rígido local** para os componentes de Implantação da Web. Conclua as etapas de instalação de alteração.