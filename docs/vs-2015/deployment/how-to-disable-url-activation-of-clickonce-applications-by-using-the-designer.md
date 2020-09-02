---
title: 'Como: desabilitar a ativação de URL de aplicativos ClickOnce usando o designer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27690ab275d0c7ef2a090fa8ef2e42887ae9daeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153805"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Como desabilitar a ativação de aplicativos ClickOnce pela URL usando o designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Normalmente, um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo será iniciado automaticamente imediatamente após ser instalado a partir de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e dizer aos usuários para iniciar o aplicativo no menu **Iniciar** em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.  
  
 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos instalados no computador do usuário a partir de um servidor Web. Ele não pode ser usado para aplicativos somente online, que só podem ser iniciados usando sua URL. Para obter mais informações sobre a diferença entre aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Esse procedimento usa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Você também pode realizar essa tarefa usando o [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Para obter mais informações, consulte [como: desabilitar a ativação de URL de aplicativos ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo  
  
1. Clique com o botão direito do mouse no nome do projeto em **Gerenciador de soluções**e clique em **Propriedades**.  
  
2. Na página **Propriedades** , clique na guia **publicar** .  
  
3. Clique em **Opções**.  
  
4. Clique em **manifestos**.  
  
5. Marque a caixa de seleção rotulada **Bloquear aplicativo para ser ativado por meio de uma URL**.  
  
6. Implante seu aplicativo.  
  
## <a name="see-also"></a>Consulte Também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
