---
title: Criar uma instalação offline | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a6a9707d517a8a43d9a9ca156a5f7291ecee9bee
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445058"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Criar uma instalação offline do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente sobre o Visual Studio, confira [Criar uma instalação offline do Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) ou [Criar uma instalação de rede do Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Esta página descreve como instalar o Visual Studio 2015 quando você não está conectado à Internet. No entanto, para executar uma instalação "desconectada", primeiro crie um layout de instalação offline usando um computador conectado à Internet. Veja como fazer isso.

> [!IMPORTANT]
> Se seu computador offline estiver executando o Windows 7 SP1 ou o Windows Server 2008 R2, confira as instruções especiais na seção [Solucionar problemas de uma instalação offline](#BKMK_tshoot) deste tópico.  Siga estas instruções *antes* de instalar o Visual Studio 2015.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a> Instalar criando uma instalação offline

#### <a name="to-create-an-offline-installation-layout"></a>Para criar um layout de instalação offline

1. Escolha a edição do Visual Studio que você deseja instalar na página de downloads [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015).

2. Depois de baixar o instalador para um local no seu sistema de arquivos, execute "\<nome do arquivo executável> /layout".

     Por exemplo, execute: `vs_enterprise.exe /layout D:\VisualStudio2015`

     Usando a opção `/layout`, você poderá baixar quase todos os pacotes de instalação, e não somente aqueles que se aplicam ao computador de download. Essa abordagem fornece os arquivos de que você precisa para executar esse instalador em qualquer lugar e poderá ser útil se você quiser instalar componentes que não foram instalados originalmente.

3. Depois da execução desse comando, é exibida uma caixa de diálogo em que é possível alterar a pasta onde você deseja que o layout de instalação offline resida.   Em seguida, clique no botão **Baixar.**

     Quando o download do pacote é bem sucedido, você deve ver uma mensagem que diz **Configuração bem sucedida! Todos os componentes especificados foram adquiridos com sucesso.**

4. Localize a pasta que você especificou anteriormente. (Por exemplo, localize D:\VisualStudio2015.) Esta pasta contém tudo o que você precisa para copiar para um local compartilhado ou instalar mídia.

    > [!CAUTION]
    > Atualmente, o SDK do Android não dá suporte a uma experiência de instalação offline. Se você instalar itens de instalação do SDK do Android em um computador que não está conectado à Internet, a instalação poderá falhar. Para saber mais, confira a seção “Solucionar problemas de uma instalação offline” neste tópico.

5. Execute a instalação a partir do local de arquivo ou da mídia de instalação.

## <a name="updating-an-offline-installation"></a>Atualizar uma instalação offline
 A Microsoft lançou várias atualizações para o Visual Studio 2015. Para atualizar sua instalação do Visual Studio, basta baixar a edição desejada na página de downloads [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015). Depois, siga as etapas descritas neste tópico para criar um novo layout de instalação offline e use-o para atualizar sua cópia do Visual Studio 2015.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a> Solucionar problemas de uma instalação offline
 Quando você faz instalação offline de seu cache de instalação offline, você pode ver mensagens de aviso sobre não ser possível instalar alguns componentes e pacotes. A tabela a seguir inclui soluções possíveis para esses cenários.

| Componente ou pacote | Solução |
|-|-|
| Dotfuscator e Analytics Community Edition 5.19.1 (para as edições Community, Professional e Enterprise do Visual Studio, como instalado no **Windows 7 SP1** e **Windows Server 2008 R2**) | Se o computador offline estiver executando o **Windows 7 SP1** ou **Windows Server 2008 R2**, execute as seguintes etapas antes de instalar o Visual Studio 2015:<br /><br /> 1. Configure um arquivo ou servidor web para baixar os arquivos CTL.<br /><br /> 2. Redirecione a URL de atualização automática da Microsoft para um ambiente desconectado.<br /><br /> Para saber mais, veja a página [Configurar raízes confiáveis e certificados não permitidos](https://technet.microsoft.com/library/dn265983.aspx) no site do Microsoft TechNet. |
| Instalação do SDK do Android (nível de API) | Você deve ter uma conexão com a Internet para instalar os pacotes de SDK do Android (nível de API). Se você estiver em uma rede restrita, será necessário permitir o acesso às seguintes URLs ao instalar o Visual Studio:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Para obter mais informações de como solucionar possíveis problemas coma configurações de proxy, confira a postagem no blog [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Falhas de instalação do Visual Studio 2015 (instalação do SDK do Android) por trás de um proxy). |
| Modelos de item de extensibilidade do Visual Studio<br /><br /> Extensão do GitHub para Visual Studio<br /><br /> PowerShell Tools for Visual Studio | Se você não tiver uma conexão com a Internet ao instalar o Visual Studio 2015, poderá usar um feed offline especial para gerar o layout de instalação offline. **Observação:** esse feed especial inclui as atualizações mais recentes para o Visual Studio 2015. <br /><br /> Para criar o feed offline especial, execute o seguinte comando: /layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*<br /><br /> Por exemplo, para um feed offline especial em inglês do Visual Studio 2015 Enterprise, execute:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Para obter uma lista completa de URLs que você pode usar para criar um feed offline de especial no idioma de sua escolha, confira a tabela a seguir. |

 Use as URLs a seguir para criar um feed offline especial específico de um idioma, conforme descrito na tabela acima.

|       Linguagem        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Chinês (Simplificado)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chinês (Tradicional) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Tcheco         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Alemão         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Inglês        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Espanhol        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francês         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italiano        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonês        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Coreano         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polonês         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Português       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Russo        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turco        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Consulte Também

- [Instalar o Visual Studio](install-visual-studio-2015.md)