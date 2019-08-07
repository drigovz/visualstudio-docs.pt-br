---
title: Emails pessoais exibidos no VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: 'As assinaturas do Visual Studio: por que estou vendo endereços do Hotmail ou do Gmail para os assinantes?'
ms.openlocfilehash: 8418a177e793f0b4fe9a5019d2cf62fa724312ff
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605761"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Assinaturas do Visual Studio: por que estão aparecendo endereços do Hotmail ou do Gmail para os assinantes?
Após as empresas migrarem do VLSC (Centro de Serviços de Licenciamento por Volume) para o novo [portal de administração de assinaturas](https://manage.visualstudio.com) do Visual Studio, os administradores ficaram surpresos ao descobrir que o "Endereço de Email de Entrada" para alguns assinantes mostra um endereço de email de terceiros, como o Hotmail, Gmail ou Yahoo.  Para saber mais, confira [este vídeo](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Causa
Esse cenário ocorre devido aos processos de entrada que estavam associados à experiência herdada de assinante do MSDN. Os usuários foram migrados do VLSC para o portal de administração de assinaturas do Visual Studio sem modificações. Os administradores talvez não soubessem que os usuários estavam usando contas pessoais para acessar os benefícios de assinatura. Antes das migrações de assinante do Visual Studio, que foram concluídas em 2016, havia duas ações necessárias para usar com êxito uma assinatura do Visual Studio:
1. O administrador "atribuiu" a assinatura a um assinante individual, usando o endereço de email corporativo ou de estudante.
2. O assinante "ativou" a assinatura.

Durante o processo de ativação de assinante: Uma MSA (conta da Microsoft) era necessária para entrar. Se o assinante não tiver tentado tornar a conta corporativa ou de estudante (por exemplo, tasha@contoso.com) uma MSA, ele poderá criar uma nova MSA ou usar uma existente. Isso fez com que o "Endereço de Email de Entrada" fosse diferente do "Endereço de Email Atribuído".

> [!NOTE]
> A nova experiência de assinante em [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) é compatível com os tipos de identidade corporativa/de estudante da conta da Microsoft (MAA).

Por fim, como a migração do administrador estava obtendo dados do VLSC sobre o "Endereço de Email de Entrada" do assinante para popular a nova experiência de gerenciamento de assinante, administradores migrados recentemente podem ter visto essas contas pessoais anteriormente despercebidas devido a alterações na interface do usuário que tornaram essas informações mais visíveis.

## <a name="solution"></a>Solução
Para corrigir o problema, você precisará editar as informações do assinante para atualizar os endereços de email de entrada.  Podem ser feitas edições em assinantes individuais ou em massa. Para obter mais informações, acesse [Editar assinaturas](edit-license.md).

##  <a name="next-steps"></a>Próximas etapas
- Se você atualizou os endereços de email de assinantes, convém notificá-los de que as informações de conexão deles foram alteradas.  Você também receberá um email com essas informações atualizadas.
- Pode ser útil [filtrar a lista de assinantes](search-license.md) em sua organização para procurar por quaisquer endereços de email de entrada que precisem ser alterados.  

