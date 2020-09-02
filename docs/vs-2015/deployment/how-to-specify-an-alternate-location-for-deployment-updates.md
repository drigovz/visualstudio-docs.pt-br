---
title: Como especificar um local alternativo para atualizações de implantação | Microsoft Docs
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
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037214"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Como especificar um local alternativo para atualizações da implantação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode instalar seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo inicialmente de um CD ou de um compartilhamento de arquivos, mas o aplicativo deve verificar se há atualizações periódicas na Web. Você pode especificar um local alternativo para as atualizações em seu manifesto de implantação para que seu aplicativo possa se atualizar da Web após a instalação inicial.  
  
> [!NOTE]
> Seu aplicativo deve ser configurado para ser instalado localmente para usar esse recurso. Para obter mais informações, consulte [Walkthrough: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Além disso, se você instalar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo da rede, definir um local alternativo fará com [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] que o use esse local para a instalação inicial e todas as atualizações subsequentes. Se você instalar o aplicativo localmente (por exemplo, de um CD), a instalação inicial será executada usando a mídia original e todas as atualizações subsequentes usarão o local alternativo.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificando um local alternativo para atualizações usando o MageUI.exe (utilitário baseado em Windows Forms)  
  
1. Abra um prompt de comando .NET Framework e digite:  
  
     **mageui.exe**  
  
2. No menu **arquivo** , escolha **abrir** para abrir o manifesto de implantação do aplicativo.  
  
3. Selecione a guia **Opções de implantação** .  
  
4. Na caixa de texto denominada **local de inicialização**, insira a URL para o diretório que conterá o manifesto de implantação para atualizações de aplicativo.  
  
5. Salve o manifesto de implantação.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Especificando um local alternativo para atualizações usando Mage.exe  
  
1. Abra um prompt de comando .NET Framework.  
  
2. Defina o local de atualização usando o comando a seguir. Neste exemplo, **HelloWorld.exe. Application** é o caminho para o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto do aplicativo, que sempre tem a extensão. Application e `http://adatum.com/Update/Path` é a URL que verificará se há [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] atualizações do aplicativo.  
  
     **Mage-Update HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/Update/Path**  
  
3. Salve o arquivo.  
  
    > [!NOTE]
    > Agora você precisa assinar novamente o arquivo com Mage.exe. Para obter mais informações, consulte [Walkthrough: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você instalar seu aplicativo de um meio offline, como um CD, e o computador estiver online, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] primeiro o verificará a URL especificada pela `<deploymentProvider>` marca no manifesto de implantação para determinar se o local de atualização contém uma versão mais recente do aplicativo. Se tiver, o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalará o aplicativo diretamente de lá, em vez do diretório de instalação inicial, e o Common Language Runtime (CLR) determinará o nível de confiança do aplicativo usando `<deploymentProvider>` . Se o computador estiver offline ou `<deploymentProvider>` inacessível, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] o instalará a partir do CD e o CLR concederá confiança com base no ponto de instalação; para uma instalação em CD, isso significará que seu aplicativo recebe confiança total. Todas as atualizações subsequentes herdarão esse nível de confiança.  
  
 Todos os [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos que usam `<deploymentProvider>` devem declarar explicitamente as permissões de que precisam no manifesto do aplicativo, para que o aplicativo não receba diferentes níveis de confiança em computadores diferentes.  
  
## <a name="see-also"></a>Consulte Também  
 [Walkthrough: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
