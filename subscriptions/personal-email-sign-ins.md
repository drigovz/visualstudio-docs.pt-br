---
title: Emails pessoais exibidos no VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 04/10/2020
ms.topic: conceptual
description: 'As assinaturas do Visual Studio: por que estou vendo endereços do Hotmail ou do Gmail para os assinantes?'
ms.openlocfilehash: 44b18bd46d55349fae5a3ece03cee9fe93240148
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223678"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Assinaturas do Visual Studio – Por que vejo contas pessoais para meus assinantes?
Depois que as empresas migraram do Centro de Serviços de Licenciamento de Volume (VLSC) para o novo Portal de Administração de Assinaturas do Visual Studio, os administradores ficaram [surpresos](https://manage.visualstudio.com)ao descobrir que o "Endereço de e-mail de login" para alguns assinantes mostra um endereço de e-mail pessoal como Hotmail ou Outlook.  

## <a name="cause"></a>Causa
Esse cenário ocorre devido aos processos de entrada que estavam associados à experiência herdada de assinante do MSDN. Os usuários foram migrados do VLSC para o portal de administração de assinaturas do Visual Studio sem modificações. Os administradores talvez não soubessem que os usuários estavam usando contas pessoais para acessar os benefícios de assinatura. Antes das migrações de assinante do Visual Studio, que foram concluídas em 2016, havia duas ações necessárias para usar com êxito uma assinatura do Visual Studio:
1. O administrador "atribuiu" a assinatura a um assinante individual, usando o endereço de email corporativo ou de estudante.
2. O assinante "ativou" a assinatura.

Durante o processo de ativação do assinante: uma Conta da Microsoft (MSA) foi necessária para entrar. Se o assinante não tiver tentado tornar a conta corporativa ou de estudante (por exemplo, tasha@contoso.com) uma MSA, ele poderá criar uma nova MSA ou usar uma existente. Isso fez com que o "Endereço de Email de Entrada" fosse diferente do "Endereço de Email Atribuído".

> [!NOTE]
> A experiência moderna [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) do assinante suporta os tipos de identidade Work/School e Microsoft Account (MSA).

## <a name="solution"></a>Solução

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

Para corrigir o problema, basta selecionar o botão **Conectar e-mails** e o sistema tentará combinar as contas com os MSAs com os usuários existentes no Azure Active Directory (Azure AD) da sua organização com base na correspondência do primeiro e sobrenome. Se houver um erro, você pode remover qualquer partida clicando no **X** à direita da partida.  

> [!div class="mx-imgBorder"]
> ![Botão Conectar e-mails](_img/connect-emails/connect-emails-button.png)

Você também pode usar o **Diretório de Pesquisa** para corrigir os erros ou preencher informações ausentes do seu Azure AD. Se todas as correspondências parecerem corretas, você pode optar por "Selecionar todos os assinantes correspondentes", em vez de selecioná-los um de cada vez.  

> [!div class="mx-imgBorder"]
> ![Conecte e-mails fly-out](_img/connect-emails/connect-emails-flyout.png)

Em seguida, clique em "continuar" que o levará a uma tela delineando as alterações a serem realizadas. Se você concordar, clique em "salvar" e as alterações serão feitas. Seu assinante também receberá uma mensagem informando-os da mudança na próxima vez que fizer login em sua assinatura.   

> [!div class="mx-imgBorder"]
> ![Conecte a confirmação de e-mails](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Quando você edita o sinal no endereço de e-mail, isso só https://my.visualstudio.comatualiza o e-mail usado pelo assinante para fazer login em sua assinatura em . Se o assinante já ativou benefícios como o Azure ou o Pluralsight usando o outro endereço de e-mail, ele precisará continuar a usar esses endereços de e-mail para acessá-los. Para quaisquer novos benefícios que eles acessam, eles devem usar o novo endereço de e-mail. 

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Próximas etapas
- Se você atualizou os endereços de email de assinantes, convém notificá-los de que as informações de conexão deles foram alteradas.  Você também receberá um email com essas informações atualizadas.
- Pode ser útil [filtrar a lista de assinantes](search-license.md) em sua organização para procurar por quaisquer endereços de email de entrada que precisem ser alterados.  
