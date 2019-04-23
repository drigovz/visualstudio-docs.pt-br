---
title: 'Como: Especificar um local alternativo para atualizações de implantação | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fafeeb386e1dd40067620d529cb25023d3f0f29
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087931"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Como: Especificar um local alternativo para as atualizações de implantação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode instalar seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo inicialmente a partir de um CD ou um compartilhamento de arquivos, mas o aplicativo deve verificar se há atualizações periódicas na Web. Você pode especificar um local alternativo para atualizações em seu manifesto de implantação para que seu aplicativo pode se atualizar da Web após sua instalação inicial.  
  
> [!NOTE]
>  Seu aplicativo deve ser configurado para instalar localmente para usar esse recurso. Para obter mais informações, confira [Passo a passo: Como implantar manualmente aplicativos ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Além disso, se você instalar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo de rede, configuração de um local alternativo faz com que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] para usar esse local para a instalação inicial e todas as atualizações subsequentes. Se você instalar o aplicativo localmente (por exemplo, a partir de um CD), a instalação inicial é executada usando a mídia original e todas as atualizações subsequentes usarão o local alternativo.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificando um local alternativo para atualizações usando o MageUI.exe (utilitário baseado em Windows Forms)  
  
1. Abra um prompt de comando do .NET Framework e digite:  
  
     **mageui.exe**  
  
2. Sobre o **arquivo** menu, escolha **abrir** para abrir o manifesto de implantação do seu aplicativo.  
  
3. Selecione o **opções de implantação** guia.  
  
4. Na caixa de texto denominada **local da inicialização**, insira a URL para o diretório que contém o manifesto de implantação para atualizações de aplicativos.  
  
5. Salve o manifesto de implantação.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Especificando um local alternativo para atualizações usando o Mage.exe  
  
1. Abra um prompt de comando do .NET Framework.  
  
2. Defina o local de atualização usando o comando a seguir. Neste exemplo, **HelloWorld.exe.application** é o caminho para seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto do aplicativo, que sempre tem a extensão. Application, e **http://adatum.com/Update/Path** é a URL que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verificará se há atualizações de aplicativo.  
  
     **Mage-atualizar HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3. Salve o arquivo.  
  
    > [!NOTE]
    >  Agora, você precisa assinar novamente o arquivo com Mage.exe. Para obter mais informações, confira [Passo a passo: Como implantar manualmente aplicativos ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você instalar o aplicativo de uma mídia offline como um CD, e o computador está online, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] primeiro verifica a URL especificada pelo `<deploymentProvider>` marca no manifesto de implantação para determinar se o local de atualização contém uma versão mais recente das aplicativo. Se isso acontecer, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instala o aplicativo diretamente a partir daí, em vez do diretório de instalação inicial, e o common language runtime (CLR) determina a relação de confiança do seu aplicativo usando o nível `<deploymentProvider>`. Se o computador estiver offline, ou `<deploymentProvider>` estiver inacessível, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalações do CD e o CLR concede confiança com base no ponto de instalação; para uma instalação com CD, isso significa que seu aplicativo recebe confiança total. Todas as atualizações subsequentes herdará esse nível de confiança.  
  
 Todos os [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos que usam `<deploymentProvider>` deve declarar explicitamente as permissões necessárias no manifesto do aplicativo, para que o aplicativo não receberá diferentes níveis de confiança em computadores diferentes.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
