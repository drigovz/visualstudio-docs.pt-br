---
title: Entrar nos serviços WCF | Microsoft Docs
description: Entrar em um serviço de Windows Communication Foundation (WCF). Se estiver na mesma solução do Visual Studio que o cliente, clique em pontos de interrupção dentro do serviço WCF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 428f5576b595797605abff2ebc5f4669e2927389
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150724"
---
# <a name="how-to-step-into-wcf-services"></a>Como intervir em serviços WCF
No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], você pode entrar em um serviço WCF. Se o serviço WCF estiver na mesma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que o cliente, você poderá usar pontos de interrupção no serviço WCF.

 Para que a depuração funcione, você deve ter a depuração habilitada no arquivo app.config ou Web.config. Para obter informações sobre como habilitar a depuração e limitações sobre a depuração nos serviços WCF, consulte [limitações na depuração do WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Para entrar em um serviço WCF

1. Crie uma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contém os projetos de cliente WCF e serviço WCF.

2. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto Cliente WCF e clique em **Definir como projeto de inicialização**.

3. Habilite a depuração no arquivo app.config ou web.config. Para obter mais informações, consulte [limitações na depuração do WCF](../debugger/limitations-on-wcf-debugging.md).

4. Defina um ponto de interrupção no local no projeto de cliente onde você deseja iniciar a entrada. Normalmente, isso será imediatamente antes da chamada de WCF.

5. Execute o ponto de interrupção e inicie a entrada. O depurador entrará no serviço automaticamente.

## <a name="see-also"></a>Confira também
- [Depurando serviços WCF](../debugger/debugging-wcf-services.md)
- [Limitações na depuração do WCF](../debugger/limitations-on-wcf-debugging.md)
- [Como depurar um serviço WCF Self-Hosted](../debugger/how-to-debug-a-self-hosted-wcf-service.md)