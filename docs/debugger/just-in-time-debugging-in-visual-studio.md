---
title: Desabilitar o depurador just-in-time | Microsoft Docs
description: A caixa de diálogo depurador just-in-time pode ser aberta quando ocorre um erro em um aplicativo. Saiba o que você pode fazer quando isso acontece e maneiras de evitá-lo.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670809ea2c9ef04107dbec5634f40831b68b94c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931494"
---
# <a name="disable-the-just-in-time-debugger"></a>Desabilitar o Depurador Just-In-Time

A caixa de diálogo depurador just-in-time pode ser aberta quando ocorre um erro em um aplicativo em execução e impede que o aplicativo continue.

O depurador just-in-time oferece a opção de iniciar o Visual Studio para depurar o erro. Você deve ter o Visual Studio ou outro depurador selecionado instalado para exibir informações detalhadas sobre o erro ou tentar depurá-lo.

Se você já é um usuário do Visual Studio e deseja tentar depurar o erro, consulte [depurar usando o depurador just-in-time](../debugger/debug-using-the-just-in-time-debugger.md). Se você não conseguir corrigir o erro ou desejar manter o depurador just-in-time de aberto, poderá desabilitar a [depuração Just-in-time do Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Se você tiver instalado o Visual Studio, mas não fizer mais, talvez seja necessário [desabilitar a depuração Just-in-time do registro do Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Se você não tiver o Visual Studio instalado, poderá evitar a depuração Just-in-time desabilitando a depuração de script ou a depuração no lado do servidor.

- Se você estiver tentando executar um aplicativo Web, desabilite a depuração de script:

  Nas opções de rede e Internet do **painel de controle** do Windows  >    >  , selecione **Desabilitar depuração de script (Internet Explorer)** e **Desabilitar depuração de script (outros)**. As etapas e configurações exatas dependem da sua versão do Windows e do seu navegador.

  ![Opções de Internet JIT](../debugger/media/jitinternetoptions.png "Opções de Internet JIT")

- Se você estiver hospedando um aplicativo Web ASP.NET no IIS, desabilite a depuração no lado do servidor:

  1. Na exibição de **recursos** do Gerenciador do IIS, na seção **ASP.net** , clique duas vezes em **compilação .net** ou selecione-a e, em seguida, selecione **abrir recurso** no painel **ações** .
  1. Em   >  **depuração** de comportamento, selecione **false**. As etapas são diferentes em versões mais antigas do IIS.

Depois de desabilitar a depuração Just-in-time, o aplicativo pode ser capaz de lidar com o erro e executar normalmente.

Se o aplicativo ainda tiver um erro sem tratamento, você poderá ver uma mensagem de erro ou o aplicativo poderá falhar ou parar de responder. O aplicativo não será executado normalmente até que o erro seja corrigido. Você pode tentar entrar em contato com o proprietário do aplicativo e pedir que ele o corrija.
