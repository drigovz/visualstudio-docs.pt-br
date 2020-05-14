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
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037214"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Como especificar um local alternativo para atualizações da implantação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalar seu aplicativo inicialmente a partir de um CD ou um compartilhamento de arquivos, mas o aplicativo deve verificar se há atualizações periódicas na Web. Você pode especificar um local alternativo para atualizações em seu manifesto de implantação para que seu aplicativo possa se atualizar da Web após sua instalação inicial.  
  
> [!NOTE]
> Seu aplicativo deve ser configurado para instalar localmente para usar esse recurso. Para obter mais informações, consulte [Passo a Passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Além disso, se [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] você instalar um aplicativo da [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rede, a configuração de um local alternativo faz com que o local use esse local tanto para a instalação inicial quanto para todas as atualizações subsequentes. Se você instalar seu aplicativo localmente (por exemplo, a partir de um CD), a instalação inicial será realizada usando a mídia original, e todas as atualizações subseqüentes usarão o local alternativo.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificando um local alternativo para atualizações usando o MageUI.exe (utilitário baseado no Windows Forms)  
  
1. Abra um prompt de comando .NET Framework e digite:  
  
     **mageui.exe**  
  
2. No menu **Arquivo,** escolha **Abrir** para abrir o manifesto de implantação do aplicativo.  
  
3. Selecione a guia **Opções de implantação.**  
  
4. Na caixa de texto chamada **Local de lançamento,** digite a URL no diretório que conterá o manifesto de implantação para atualizações de aplicativos.  
  
5. Salve o manifesto de implantação.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Especificando um local alternativo para atualizações usando Mage.exe  
  
1. Abra um prompt de comando .NET Framework.  
  
2. Defina o local de atualização usando o seguinte comando. Neste exemplo, **helloWorld.exe.application** é o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] caminho para o manifesto do seu `http://adatum.com/Update/Path` aplicativo, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] que sempre tem a extensão .application, e é a URL que verificará as atualizações do aplicativo.  
  
     **Mago -Atualização HelloWorld.exe.application -ProviderUrl\/http: /adatum.com/Update/Path**  
  
3. Salve o arquivo.  
  
    > [!NOTE]
    > Agora você precisa assinar novamente o arquivo com Mage.exe. Para obter mais informações, consulte [Passo a Passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você instalar seu aplicativo a partir de um meio offline, como um CD, e o computador estiver on-line, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] primeiro verifique a URL especificada pela `<deploymentProvider>` tag no manifesto de implantação para determinar se o local de atualização contém uma versão mais recente do aplicativo. Se isso [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] acontecer, instala o aplicativo diretamente a partir daí, em vez de a partir do diretório inicial de `<deploymentProvider>`instalação, e o tempo de execução do idioma comum (CLR) determina o nível de confiança do aplicativo usando . Se o computador estiver `<deploymentProvider>` off-line [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ou não for inalcançável, será instalado a partir do CD e a CLR conceder á confiança com base no ponto de instalação; para uma instalação de CD, isso significa que seu aplicativo recebe total confiança. Todas as atualizações subseqüentes herdarão esse nível de confiança.  
  
 Todos [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] os aplicativos `<deploymentProvider>` que usam devem declarar explicitamente as permissões necessárias em seu manifesto de aplicação, para que o aplicativo não receba diferentes níveis de confiança em diferentes computadores.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
