---
title: Emails pessoais exibidos no VLSC
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 09/17/2020
ms.topic: conceptual
description: 'As assinaturas do Visual Studio: por que estou vendo endereços do Hotmail ou do Gmail para os assinantes?'
ms.openlocfilehash: c7a5546a99ed73175ab0f4af2c22b3cbf20c0bdd
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006066"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Assinaturas do Visual Studio – por que vejo contas pessoais para meus assinantes?
Depois que as empresas migraram do VLSC (Volume Licensing Service Center) para o novo [portal de administração de assinaturas](https://manage.visualstudio.com)do Visual Studio, os administradores ficaram surpresos em descobrir que o "endereço de email de entrada" para alguns assinantes mostra um endereço de email pessoal como o hotmail ou o Outlook.  

## <a name="cause"></a>Causa
Esse cenário ocorre devido aos processos de entrada que estavam associados à experiência herdada de assinante do MSDN. Os usuários foram migrados do VLSC para o portal de administração de assinaturas do Visual Studio sem modificações. Os administradores talvez não soubessem que os usuários estavam usando contas pessoais para acessar os benefícios de assinatura. Antes das migrações de assinante do Visual Studio, que foram concluídas em 2016, havia duas ações necessárias para usar com êxito uma assinatura do Visual Studio:
1. O administrador "atribuiu" a assinatura a um assinante individual, usando o endereço de email corporativo ou de estudante.
2. O assinante "ativou" a assinatura.

Durante o processo de ativação do assinante: uma Conta da Microsoft (MSA) foi necessária para entrar. Se o assinante não tiver tentado tornar a conta corporativa ou de estudante (por exemplo, tasha@contoso.com) uma MSA, ele poderá criar uma nova MSA ou usar uma existente. Isso fez com que o "Endereço de Email de Entrada" fosse diferente do "Endereço de Email Atribuído".

> [!NOTE]
> A experiência moderna do Assinante no [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) dá suporte aos tipos de identidade de trabalho/escola e da MSA (conta da Microsoft).

## <a name="solution"></a>Solução

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

Para corrigir o problema, basta selecionar o botão **conectar emails** e o sistema tentará corresponder as contas com MSAS aos usuários existentes no Azure Active Directory da sua organização (AD do Azure) com base na correspondência do nome e sobrenome. Se houver um erro, você poderá remover qualquer correspondência clicando no **X** à direita da correspondência.  

> [!div class="mx-imgBorder"]
> ![Botão conectar emails](_img/connect-emails/connect-emails-button.png "Clique em conectar emails para corresponder aos usuários com contas da Microsoft ao seu Azure Active Directory")

Você também pode usar o **diretório de pesquisa** para corrigir os erros ou preencher as informações ausentes do seu Azure AD. Se todas as correspondências estiverem corretas, você poderá optar por "selecionar todos os assinantes correspondentes", em vez de selecioná-los um de cada vez.  

> [!div class="mx-imgBorder"]
> ![Sair do Connect de emails](_img/connect-emails/connect-emails-flyout.png "Selecione os assinantes que você deseja corresponder às suas identidades do Azure AD e clique em continuar.")

Em seguida, clique em "continuar", que o levará para uma lista das alterações a serem realizadas. Se você concordar, clique em "salvar" e as alterações serão feitas. Seu assinante também receberá uma mensagem informando a alteração na próxima vez que entrar em sua assinatura.   

> [!div class="mx-imgBorder"]
> ![Confirmação de conexão de emails](_img/connect-emails/connect-emails-confirm.png "Clique em continuar para implementar as alterações propostas e, em seguida, clique em salvar.") 

> [!NOTE]
> Quando você edita o endereço de email de entrada, isso atualiza apenas o email usado pelo assinante para entrar em sua assinatura no https://my.visualstudio.com . Se o Assinante já tiver ativado os benefícios como o Azure ou o Pluralsight usando o outro endereço de email, eles precisarão continuar a usar esses endereços de email para acessá-los. Para quaisquer benefícios novos que eles acessam, eles devem usar o novo endereço de email. 

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](/visualstudio/)
- [Documentação do Azure DevOps](/azure/devops/)
- [Documentação do Azure](/azure/)
- [Documentação do Microsoft 365](/microsoft-365/)

##  <a name="next-steps"></a>Próximas etapas
- Se você atualizou os endereços de email de assinantes, convém notificá-los de que as informações de conexão deles foram alteradas.  Você também receberá um email com essas informações atualizadas.
- Pode ser útil [filtrar a lista de assinantes](search-license.md) em sua organização para procurar por quaisquer endereços de email de entrada que precisem ser alterados.