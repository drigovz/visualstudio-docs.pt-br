---
title: 'Como: Desabilitar a ativação de aplicativos ClickOnce pela URL | Microsoft Docs'
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
ms.openlocfilehash: c22128d20bf83a8c6f2295b79653eabb3439c4b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928818"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Como: Desabilitar a ativação de URL de aplicativos ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Normalmente, um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo será iniciado automaticamente, imediatamente após a instalação de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e diga aos usuários para iniciar o aplicativo a partir de **iniciar** menu em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.  
  
 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos instalados no computador do usuário de um servidor Web. Ele não pode ser usado para aplicativos somente online, que podem ser iniciados apenas por meio de sua URL. Para obter mais informações sobre a diferença entre os aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimento usa o [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] MageUI.exe de ferramentas. Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Você também pode executar esse procedimento usando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo  
  
1.  Abra o manifesto de implantação no MageUI.exe. Se você não ainda tiver criado uma, siga as etapas em [passo a passo: Como implantar manualmente aplicativos ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Selecione o **opções de implantação** guia.  
  
3.  Desmarque a **executar o aplicativo depois de instalar automaticamente** caixa de seleção.  
  
4.  Salve e assinar o manifesto.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
