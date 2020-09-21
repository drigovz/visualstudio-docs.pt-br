---
title: Escolhendo uma estratégia de implantação do ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cce51860b335e16fe507b20e41a5adba0b3fa278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838476"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Escolhendo uma estratégia de implantação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Há três estratégias diferentes para implantar um aplicativo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]; a estratégia escolhida depende principalmente do tipo de aplicativo que você está implantando. As três estratégias de implantação são as seguintes:  
  
- Instalação da Web ou de um compartilhamento de rede  
  
- Instalação de um CD  
  
- Iniciação do aplicativo da Web ou de um compartilhamento de rede  
  
    > [!NOTE]
    > Além de selecionar uma estratégia de implantação, talvez você também deseje selecionar uma estratégia para fornecer atualizações do aplicativo. Para obter mais informações, confira [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Instalação da Web ou de um compartilhamento de rede  
 Quando você usa essa estratégia, o aplicativo é implantado em um servidor Web ou compartilhamento de arquivos de rede. Quando um usuário final desejar instalar o aplicativo, ele clicará em um ícone em uma página da Web ou clicará duas vezes em um ícone no compartilhamento de arquivos. O aplicativo é baixado e, em seguida, instalado e iniciado no computador do usuário final. Os itens são adicionados ao menu **Iniciar** e **Adicionar** ou **Remover Programas** no Painel de Controle.  
  
 Como essa estratégia depende de conectividade de rede, ela funcionará melhor para aplicativos que serão implantados para usuários com acesso a uma rede local ou a uma conexão com a Internet de alta velocidade.  
  
 Se você implantar o aplicativo da Web, poderá passar argumentos para o aplicativo quando ele for ativado por meio de uma URL. Para obter mais informações, consulte [como recuperar informações de cadeia de caracteres de consulta em um aplicativo ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Você não poderá passar argumentos para um aplicativo ativado ao usar qualquer um dos outros métodos descritos neste documento.  
  
 Para habilitar essa estratégia de implantação em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], clique em **Da Web** ou **De um caminho UNC ou compartilhamento de arquivos** na página **Como Instalado** do Assistente de Publicação.  
  
 Essa é a estratégia de implantação padrão.  
  
## <a name="install-from-a-cd"></a>Instalação de um CD  
 Ao usar essa estratégia, seu aplicativo será implantado em mídia removível como um CD-ROM ou DVD. Como na opção anterior, quando o usuário opta por instalar o aplicativo, ele é instalado e iniciado e os itens são adicionados ao menu **Iniciar** e **Adicionar ou Remover Programas** no **Painel de Controle**.  
  
 Essa estratégia funcionará melhor para aplicativos que serão implantados para usuários sem conectividade de rede persistente ou com conexões de baixa largura de banda. Como o aplicativo é instalado de mídia removível, nenhuma conexão de rede é necessária para instalação; no entanto, conectividade de rede ainda é necessária para atualizações do aplicativo.  
  
 Para habilitar essa estratégia de implantação em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], clique em **De um CD-ROM ou DVD-ROM** na página **Como Instalado** do Assistente de Publicação.  
  
 Para habilitar essa estratégia de implantação manualmente, altere a tag **deploymentProvider** no manifesto de implantação. (No Visual Studio, essa propriedade é exposta como **URL de Instalação** na página **Publicar** do Designer de Projeto. Em Mage.exe, ela é **Localização Inicial**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Iniciação do aplicativo da Web ou de um compartilhamento de rede  
 Esta estratégia é como a primeira, exceto que o aplicativo se comporta como um aplicativo Web. Quando o usuário clica em um link em uma página da Web (ou clica duas vezes em um ícone no compartilhamento de arquivos), o aplicativo é iniciado. Quando os usuários fecharem o aplicativo, ele não estará mais disponível em seus computadores locais; nada será adicionado ao menu **Iniciar** ou **Adicionar ou Remover Programas** no **Painel de Controle**.  
  
> [!NOTE]
> Tecnicamente, o aplicativo será baixado e instalado em um cache de aplicativos no computador local, exatamente como um aplicativo Web é baixado no cache da Web. Como no cache da Web, os arquivos serão eventualmente removidos do cache de aplicativos. No entanto, a percepção do usuário é que o aplicativo está sendo executado da Web ou do compartilhamento de arquivos.  
  
 Essa estratégia funciona melhor para aplicativos que são usados com pouca frequência, por exemplo, uma ferramenta de benefícios de funcionários que é normalmente executada apenas uma vez por ano.  
  
 Para habilitar essa estratégia de implantação em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], clique em **Não instalar o aplicativo** na página **Instalar ou Executar da Web** do Assistente de Publicação.  
  
 Para habilitar essa estratégia de implantação, manualmente, altere a tag **install** no manifesto de implantação. (Seu valor pode ser **true** ou **false**. Em Mage.exe, use a opção **somente online** na lista **tipo de aplicativo** .)  
  
## <a name="web-browser-support"></a>Suporte a navegadores da Web  
 Os aplicativos destinados ao .NET Framework 3.5 podem ser instalados usando qualquer navegador.  
  
 Os aplicativos destinados ao .NET Framework 2.0 exigem o Internet Explorer.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
