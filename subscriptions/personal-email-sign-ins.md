---
title: Emails pessoais exibidos no VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: 'As assinaturas do Visual Studio: por que estou vendo endereços do Hotmail ou do Gmail para os assinantes?'
ms.openlocfilehash: c4a3202bfb14246fa8057309de90bdc7c32db5df
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410227"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Assinaturas do Visual Studio: por que estão aparecendo endereços do Hotmail ou do Gmail para os assinantes?
Após as empresas migrarem do VLSC (Centro de Serviços de Licenciamento por Volume) para o novo [portal de administração de assinaturas](https://manage.visualstudio.com) do Visual Studio, os administradores ficaram surpresos ao descobrir que o "Endereço de Email de Entrada" para alguns assinantes mostra um endereço de email de terceiros, como o Hotmail, Gmail ou Yahoo.  Para saber mais, confira [este vídeo](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Causa
Esse cenário ocorre devido aos processos de entrada que estavam associados à experiência herdada de assinante do MSDN. Os usuários foram migrados do VLSC para o portal de administração de assinaturas do Visual Studio sem modificações. Os administradores talvez não soubessem que os usuários estavam usando contas pessoais para acessar os benefícios de assinatura. Antes das migrações de assinante do Visual Studio, que foram concluídas em 2016, havia duas ações necessárias para usar com êxito uma assinatura do Visual Studio:
1. O administrador "atribuiu" a assinatura a um assinante individual, usando o endereço de email corporativo ou de estudante.
2. O assinante "ativou" a assinatura.

Durante o processo de ativação do assinante: uma Conta da Microsoft (MSA) foi necessária para entrar. Se o assinante não tiver tentado tornar a conta corporativa ou de estudante (por exemplo, tasha@contoso.com) uma MSA, ele poderá criar uma nova MSA ou usar uma existente. Isso fez com que o "Endereço de Email de Entrada" fosse diferente do "Endereço de Email Atribuído".

> [!NOTE]
> A nova experiência de assinante em [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) é compatível com os tipos de identidade corporativa/de estudante da conta da Microsoft (MAA).

## <a name="solution"></a>Solução
Para corrigir o problema, basta selecionar o botão **conectar emails** e o sistema tentará corresponder as contas com MSAS aos usuários existentes no Azure Active Directory da sua organização (AD do Azure) com base na correspondência do nome e sobrenome. Se houver um erro, você poderá remover qualquer correspondência clicando no **X** à direita da correspondência.  

> [!div class="mx-imgBorder"]
> Botão ![conectar emails](_img/connect-emails/connect-emails-button.png)

Você também pode usar o **diretório de pesquisa** para corrigir os erros ou preencher as informações ausentes do seu Azure AD. Se todas as correspondências estiverem corretas, você poderá optar por "selecionar todos os assinantes correspondentes", em vez de selecioná-los um de cada vez.  

> [!div class="mx-imgBorder"]
> ](_img/connect-emails/connect-emails-flyout.png) de saída de emails do ![Connect

Em seguida, clique em "continuar", que levará você para uma tela que descreve as alterações a serem realizadas. Se você concordar, clique em "salvar" e as alterações serão feitas. Seu assinante também receberá uma mensagem informando a alteração na próxima vez que entrar em sua assinatura.   

> [!div class="mx-imgBorder"]
> Confirmação de email do ![Connect](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Quando você edita o endereço de email de entrada, isso atualiza apenas o email usado para entrar em sua assinatura no https://my.visualstudio.com. Se o Assinante já tiver ativado os benefícios como o Azure ou o Pluralsight usando o outro endereço de email, eles precisarão continuar a usar esses endereços de email para acessá-los. Para quaisquer benefícios novos que eles acessam, eles devem usar o novo endereço de email. 

## <a name="see-also"></a>Consulte também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}
- Se você atualizou os endereços de email de assinantes, convém notificá-los de que as informações de conexão deles foram alteradas.  Você também receberá um email com essas informações atualizadas.
- Pode ser útil [filtrar a lista de assinantes](search-license.md) em sua organização para procurar por quaisquer endereços de email de entrada que precisem ser alterados.  
