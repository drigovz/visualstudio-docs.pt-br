---
title: Emails pessoais para assinaturas do Visual Studio no VLSC
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 10/28/2020
ms.topic: conceptual
description: 'As assinaturas do Visual Studio: por que estou vendo endereços do Hotmail ou do Gmail para os assinantes?'
ms.openlocfilehash: fda7dab50c2151049e0feffa50609bf4c38e38cc
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904252"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Assinaturas do Visual Studio – por que vejo contas pessoais para meus assinantes?
Depois que as empresas migraram do VLSC (Volume Licensing Service Center) para o novo [portal de administração de assinaturas](https://manage.visualstudio.com)do Visual Studio, os administradores ficaram surpresos em descobrir que o "endereço de email de entrada" para alguns assinantes mostra um endereço de email pessoal como o hotmail ou o Outlook.  

## <a name="cause"></a>Causa
Esse cenário ocorre devido aos processos de entrada que estavam associados à experiência herdada de assinante do MSDN. Os usuários foram migrados do VLSC para o portal de administração de assinaturas do Visual Studio sem modificações. Os administradores podem não ter consciência de que os usuários tinham usado contas pessoais para acessar seus benefícios de assinatura. Antes das migrações de assinante do Visual Studio, que foram concluídas em 2016, havia duas ações necessárias para usar com êxito uma assinatura do Visual Studio:
1. O administrador "atribuído" à assinatura para um assinante individual, usando seu endereço de email corporativo ou de estudante.
2. O assinante "ativou" a assinatura.

Durante o processo de ativação do assinante: uma Conta da Microsoft (MSA) foi necessária para entrar. Se o assinante não tiver tentado tornar a conta corporativa ou de estudante (por exemplo, tasha@contoso.com) uma MSA, ele poderá criar uma nova MSA ou usar uma existente. Isso fez com que o "Endereço de Email de Entrada" fosse diferente do "Endereço de Email Atribuído".

> [!NOTE]
> A experiência moderna do Assinante no [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) dá suporte aos tipos de identidade de trabalho/escola e da MSA (conta da Microsoft).

## <a name="solution"></a>Solução
Para corrigir o problema, basta selecionar o botão **conectar emails** e o sistema tentará corresponder as contas com MSAS aos usuários existentes no Azure Active Directory da sua organização (AD do Azure) com base na correspondência do nome e sobrenome. Se houver um erro, você poderá remover qualquer correspondência clicando no **X** à direita da correspondência.  

Assista a este vídeo ou Continue lendo para saber como corrigir isso. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![Botão conectar emails](_img/connect-emails/connect-emails-button.png "Clique em conectar emails para corresponder aos usuários com contas da Microsoft ao seu Azure Active Directory")

Você também pode usar o **diretório de pesquisa** para corrigir os erros ou preencher as informações ausentes do seu Azure AD. Se todas as correspondências estiverem corretas, você poderá escolher o botão de **identidade atual** para selecionar todas as entradas correspondentes, em vez de selecioná-las uma de cada vez.  

> [!div class="mx-imgBorder"]
> ![Sair do Connect de emails](_img/connect-emails/connect-emails-flyout.png "Selecione os assinantes que você deseja corresponder às suas identidades do Azure AD e clique em continuar.")

Em seguida, clique em **continuar** , que levará você para uma lista das alterações a serem realizadas. Se você concordar, clique em **salvar** e as alterações serão feitas. Seu assinante também receberá uma mensagem informando a alteração na próxima vez que entrar em sua assinatura.  Observe que apenas os dois assinantes que foram correspondidos na Azure Active Directory aparecem nessa lista.  Em nosso exemplo, como o Frederick não tinha um endereço correspondente no Azure AD, seu conta Microsoft (MSA) não foi correspondido a uma conta corporativa. 

> [!div class="mx-imgBorder"]
> ![Confirmação de conexão de emails](_img/connect-emails/connect-emails-confirm.png "Clique em continuar para implementar as alterações propostas e, em seguida, clique em salvar.") 

> [!NOTE]
> Quando você edita o endereço de email de entrada, isso atualiza apenas o email usado pelo assinante para entrar em sua assinatura no https://my.visualstudio.com . Se o Assinante já tiver ativado os benefícios como o Azure ou o Pluralsight usando o outro endereço de email, eles precisarão continuar a usar esses endereços de email para acessá-los. Para quaisquer benefícios novos que eles acessam, eles devem usar o novo endereço de email. 

## <a name="see-also"></a>Veja também
- [Documentação do Visual Studio](/visualstudio/)
- [Documentação do Azure DevOps](/azure/devops/)
- [Documentação do Azure](/azure/)
- [Documentação do Microsoft 365](/microsoft-365/)

##  <a name="next-steps"></a>Próximas etapas
- Se você atualizou os endereços de email de assinantes, convém notificá-los de que as informações de conexão deles foram alteradas.  Você também receberá um email com essas informações atualizadas.
- Pode ser útil [filtrar a lista de assinantes](search-license.md) em sua organização para procurar por quaisquer endereços de email de entrada que precisem ser alterados.