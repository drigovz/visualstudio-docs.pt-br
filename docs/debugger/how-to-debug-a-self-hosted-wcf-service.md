---
title: 'Como: depurar um serviço WCF auto-hospedado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b9a3aa9cdec8be345929ebea0109a472e79e716
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704339"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Como depurar um serviço WCF auto-hospedado
Um *serviço auto-hospedado* é um serviço WCF que não é executado dentro do IIS, do Host de Serviço WCF ou do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. A maneira mais fácil de depurar um WCF auto-hospedado é configurar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar o cliente e o servidor quando você escolher **Iniciar Depuração** no menu **Depurar**.

 Se o serviço WCF está sendo auto-hospedado internamente ou é um processo que não pode ser iniciado dessa maneira, como serviço do NT, você não pode usar este método. Em vez disso, execute um destes procedimentos:

-   Anexe manualmente o depurador ao processo de hospedagem. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     – ou —

-   Inicie a depuração do cliente e inspecione uma chamada para o serviço. Isso requer que você habilite a depuração no arquivo app.config. Para obter mais informações, [limitações na depuração de WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Para iniciar o cliente e o host do Visual Studio

1. Crie uma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contém os projetos de cliente e de servidor.

2. Configure a solução para iniciar os processos do cliente e do servidor quando você escolhe **Iniciar** no menu **Depurar**.

   1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome da solução.

   2.  Clique em **Definir Projetos de Inicialização**.

   3.  Na caixa de diálogo **Propriedades da Solução \<nome>**, selecione **Vários Projetos de Inicialização**.

   4.  Na grade **Vários Projetos de Inicialização**, na linha que corresponde ao projeto do servidor, clique em **Ação** e escolha **Iniciar**.

   5.  Na linha que corresponde ao projeto de cliente, clique em **Ação** e escolha **Iniciar**.

   6.  Clique em **OK**.

## <a name="see-also"></a>Consulte também
- [Depurando serviços WCF](../debugger/debugging-wcf-services.md)
- [Limitações da depuração de WCF](../debugger/limitations-on-wcf-debugging.md)
- [Como intervir em serviços WCF](../debugger/how-to-step-into-wcf-services.md)