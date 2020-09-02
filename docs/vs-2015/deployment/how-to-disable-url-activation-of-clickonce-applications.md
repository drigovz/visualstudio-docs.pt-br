---
title: Como desabilitar a ativação de URL de aplicativos ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a98706858323693ec01ec3c3420a6d2d25ffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697221"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Como desabilitar a ativação de aplicativos ClickOnce pela URL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Normalmente, um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo será iniciado automaticamente imediatamente após ser instalado a partir de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e informar os usuários para iniciar o aplicativo no menu **Iniciar** em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.  
  
 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos instalados no computador do usuário a partir de um servidor Web. Ele não pode ser usado para aplicativos somente online, que só podem ser iniciados usando sua URL. Para obter mais informações sobre a diferença entre aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimento usa a [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] ferramenta MageUI.exe. Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe (manifest Generation and Editing Tool, cliente gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Você também pode executar esse procedimento usando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo  
  
1. Abra seu manifesto de implantação no MageUI.exe. Se você ainda não tiver criado uma, siga as etapas descritas em [Walkthrough: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Selecione a guia **Opções de implantação** .  
  
3. Desmarque a caixa de seleção **Executar aplicativo automaticamente após a instalação** .  
  
4. Salve e assine o manifesto.  
  
## <a name="see-also"></a>Consulte Também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
