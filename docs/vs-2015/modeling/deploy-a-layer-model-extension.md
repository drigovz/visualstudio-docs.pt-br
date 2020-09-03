---
title: Implantar uma extensão de modelo de camada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669869"
---
# <a name="deploy-a-layer-model-extension"></a>Implantar uma extensão de modelo de camada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Outros usuários do Visual Studio podem instalar extensões de modelagem de camada que você cria usando o Visual Studio.

## <a name="installing-your-extension"></a>Instalando sua extensão
 Sua extensão é compilada em um arquivo VSIX, que pode ser instalado em outros computadores. Você também pode instalá-lo em seu computador de desenvolvimento, para disponibilizar a extensão na instância principal do Visual Studio.

#### <a name="to-install-the-extension"></a>Para instalar a extensão

1. No projeto que contém **Source. vsix. manifest**, abra **bin \\ \\ *** no explorador de arquivos.

2. Copie o arquivo ** \* . vsix** para o computador no qual você deseja instalar a extensão.

3. No computador de destino, clique duas vezes no arquivo *. vsix no Windows Explorer.

    O instalador do VSIX é aberto.

#### <a name="to-uninstall-the-extension"></a>Para desinstalar a extensão

1. No Visual Studio, no menu **ferramentas** , clique em **extensões e atualizações**.

2. Clique no nome da extensão e, em seguida, clique em **desinstalar**.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalando uma extensão em um Team Foundation Build Server
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] os servidores normalmente não têm o Visual Studio instalado e, portanto, não é possível instalar o VSIX clicando duas vezes nele. A instalação do [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] inclui alguns componentes que permitem a execução de uma extensão VSIX, mas você deve instalar a extensão manualmente.

#### <a name="to-install-your-layer-extension-on-a-esprbuild-server"></a>Para instalar a extensão de camada em um [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] servidor

1. Copie os arquivos **. vsix** do seu computador de desenvolvimento para o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] computador.

     Coloque o arquivo VSIX em um dos seguintes locais:

    - Para instalar para todos os usuários e serviços:

         %ProgramFiles%\Microsoft Visual Studio [versão] \Common7\IDE\Extensions\Microsoft

    - Para instalar somente o serviço de rede que executa o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] :

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio \\ [versão] \Extensions\Microsoft

    - Se você tiver configurado [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] para ser executado no modo interativo como um usuário específico, poderá instalar apenas para esse usuário:

         %LocalAppData%\Microsoft\VisualStudio \\ [versão] \Extensions\Microsoft

        > [!NOTE]
        > % LocalAppData% normalmente é *driveName*: Users*username*AppDataLocal.

2. Expanda cada arquivo do VSIX em uma pasta no mesmo local:

    1. Altere a extensão de nome de arquivo de **. vsix** para **. zip**.

    2. Extraia o conteúdo do arquivo. zip para uma pasta.

    3. Excluir o arquivo. zip

3. Reinicie o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].
