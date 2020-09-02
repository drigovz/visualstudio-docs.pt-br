---
title: 'Como: entrar em serviços WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 951d5f39fbf3929d094cc18de5fe108b46753b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176531"
---
# <a name="how-to-step-into-wcf-services"></a>Como intervir em serviços WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], você pode entrar em um serviço WCF. Se o serviço WCF estiver na mesma solução do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que o cliente, você poderá usar pontos de interrupção no serviço WCF.  
  
 Para que a depuração funcione, você deve ter a depuração habilitada no arquivo app.config ou Web.config. Para obter informações sobre como habilitar a depuração e limitações sobre a depuração nos serviços WCF, consulte [limitações na depuração do WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Para entrar em um serviço WCF  
  
1. Crie uma solução do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contém os projetos de cliente WCF e serviço WCF.  
  
2. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto Cliente WCF e clique em **Definir como projeto de inicialização**.  
  
3. Habilite a depuração no arquivo app.config ou web.config. Para obter mais informações, consulte [limitações na depuração do WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4. Defina um ponto de interrupção no local no projeto de cliente onde você deseja iniciar a entrada. Normalmente, isso será imediatamente antes da chamada de WCF.  
  
5. Execute o ponto de interrupção e inicie a entrada. O depurador entrará no serviço automaticamente.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurando serviços WCF](../debugger/debugging-wcf-services.md)   
 [Limitações na depuração do WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Como depurar um serviço WCF auto-hospedado](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
