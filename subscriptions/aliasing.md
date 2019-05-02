---
title: A entrada nas assinaturas do Visual Studio pode falhar ao usar aliases | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: conceptual
description: A entrada poderá falhar se forem usados aliases ou nomes amigáveis
searchscope: VS Subscription
ms.openlocfilehash: ac3f9df365e0b7924b615c2ae8cbb70d93d04948
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946156"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>A entrada nas assinaturas do Visual Studio poderá falhar ao usar aliases

Dependendo do tipo de conta usado para entrar, é possível que as assinaturas disponíveis não sejam exibidas corretamente ao entrar no [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Uma possível causa é o uso de "alias" ou "nomes amigáveis" em vez da identidade à qual a assinatura foi atribuída. Isso é chamado de "alias".

## <a name="what-is-aliasing"></a>O que é um alias?

O termo "alias" refere-se a usuários com identidades diferentes para entrar no Windows (ou no Active Directory) e para acessar o email.

Os aliases podem ser encontrados quando a empresa tem um Serviço Online da Microsoft para a entrada no diretório, como JohnD@contoso.com, mas os usuários acessam as contas de email usando aliases ou nomes amigáveis, como John.Doe@contoso.com. Para muitos clientes que gerenciam as assinaturas por VLSC (Volume Licensing Service Center), isso pode resultar em uma experiência de logon malsucedida, pois o endereço de email fornecido (John.Doe@contoso.com) não coincide com o endereço do diretório (JohnD@contoso.com) necessário para a autenticação bem-sucedida por meio da opção "Conta corporativa ou de estudante".

## <a name="as-an-administrator-what-options-do-i-have"></a>Como administrador, quais opções tenho?

Como administrador, há duas opções para garantir que os assinantes entrem no [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) com sucesso.
- A primeira opção (recomendada) é utilizar a conta de diretório como o endereço atribuído no VLSC (Volume Licensing Service Center). Confira a seção [Atribuir assinantes a uma conta de diretório](#assigning-subscribers-to-a-directory-account) neste artigo para obter mais detalhes.
- A segunda opção (menos segura) é permitir que assinantes associem o endereço de email "Corporativo ou de Estudante" a uma conta "Pessoal" (também conhecido como MSA ou conta da Microsoft). Veja a seção [Definir uma conta corporativa ou de estudante como uma conta pessoal](#defining-a-work-or-school-account-as-a-personal-account) neste artigo para obter mais detalhes.

> [!NOTE]
> Depois que a empresa migrar para o novo [portal de gerenciamento](https://manage.visualstudio.com) de assinaturas do Visual Studio, você poderá aproveitar a nova experiência de administração, que permite que endereços de diretório e email sejam fornecidos como parte do perfil do assinante. Saiba mais sobre [a migração](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Como assinante, quais opções eu tenho?

Da perspectiva do assinante, é importante primeiro trabalhar com o administrador para entender a configuração de identidade da empresa. Se necessário, o administrador poderá precisar atualizar as configurações de conta no portal de administração ou talvez seja necessário criar uma MSA (conta da Microsoft) usando o endereço de email corporativo. Antes de executar as etapas para criar uma MSA, fale com o administrador sobre quaisquer políticas ou problemas na execução desta ação. Veja a seção [Definir uma conta corporativa ou de estudante como uma conta pessoal](#defining-a-work-or-school-account-as-a-personal-account) neste artigo para obter mais detalhes.

## <a name="assigning-subscribers-to-a-directory-account"></a>Atribuindo assinantes a uma conta de diretório

Em todos os casos, o Gerenciador de Assinatura no VLSC (Volume Licensing Service Center) precisará usar o endereço do diretório para novos assinantes ou atualizar o endereço de email para assinantes "existentes". É importante observar que o uso do endereço do diretório significará que quaisquer assinantes novos não receberão um Email de Boas-vindas, e o administrador precisará notificar o assinante de que uma assinatura foi atribuída a ele. Depois de seguir as etapas abaixo, também fique à vontade para usar o [modelo](#notifying-your-subscribers-with-directory-addresses) de email para notificar assinantes e ajudá-los no processo de entrada.

### <a name="adding-new-subscribers"></a>Adicionando novos assinantes

Siga estas etapas para adicionar um novo assinante com uma conta de diretório.

1. Acesse o [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (Volume Licensing Service Center) e entre.
2. Na página Administrador do VLSC, clique em **Assinaturas** e em **Assinaturas do Visual Studio**.

    > [!div class="mx-imgBorder"]
    > ![Menu de assinaturas](_img//vlsc/vlsc-subscriptions.png)

3. Clique no **Número do Contrato** associado à assinatura do Visual Studio.

    > [!div class="mx-imgBorder"]
    > ![Selecionar contrato](_img/vlsc/vlsc-agreement.png)

4. Clique em **Atribuir Assinatura**.
5. Selecione o **Nível de Assinatura** desejado.
6. Valide que você tem assinaturas disponíveis para atribuir e clique em **Avançar**.
7. Insira os detalhes do assinante e o endereço do diretório no campo Endereço de Email e clique em **Avançar**.
8. Valide as informações do assinante e clique em **Concluir**.
9. Notifique o assinante de que a assinatura foi provisionada usando o [modelo](#notifying-your-subscribers-with-directory-addresses) abaixo.

### <a name="updating-an-existing-subscriber"></a>Atualizando um assinante existente

Siga as etapas abaixo para atualizar um assinante existente com uma conta de diretório.

1. Acesse o [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (Volume Licensing Service Center) e entre.
2. Nas páginas de Administração do VLSC, clique em **Assinaturas** e em **Assinaturas do Visual Studio**.
3. Clique no **Número do Contrato** associado à assinatura do Visual Studio.
4. Clique na **seta para baixo** na barra de Pesquisa.
5. Procure o assinante usando o campo "Endereço de Email".
6. Na lista de resultados, clique no **Sobrenome** do assinante.
7. Clique em **Editar**.
8. Altere o campo Endereço de Email para o endereço do diretório desejado e clique em **Salvar**.
9. Notifique o assinante de que a assinatura foi provisionada usando o modelo de email abaixo.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Notificar assinantes com endereços de diretório

Como o Email de Boas-vindas não chegou ao assinante com êxito, copie e cole a mensagem abaixo em um email e envie-a ao assinante. Substitua %WORD% pelas informações apropriadas para cada assinante.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription. Please visit https://my.visualstudio.com, and log in with your %DIRECTORY ADDRESS% address to activate and access your subscription.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Definindo uma conta corporativa ou de estudante como uma conta pessoal

Use as instruções descritas na seção [Atribuir assinantes a uma conta de diretório](#assigning-subscribers-to-a-directory-account) para adicionar um novo usuário ou atualizar o endereço de email do usuário no VLSC (Volume Licensing Service Center).  Nos casos em que o endereço de email não for reconhecido pelo diretório, o usuário precisará realizar o processo para criar uma nova conta para definir o endereço de email como uma conta pessoal.  Em curto prazo, a equipe de Assinaturas do Visual Studio garantiu uma isenção da política de identidade definida abaixo, mas estamos investindo nos recursos necessários para remover essa política.

> [!WARNING]
> A Microsoft não recomenda a combinação de identidades "corporativas ou de estudante" a identidades "Pessoais".  Essa ação faz com que a organização a perca a propriedade e o controle da conta, e o funcionário pode continuar a acessar produtos ou serviços específicos, mesmo depois de sair da empresa.  Confira esta [postagem de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/), da equipe do Microsoft Identity, para obter informações adicionais.

### <a name="defining-an-email-address-as-a-personal-account"></a>Definindo um endereço de email como uma conta pessoal

Depois que uma assinatura for atribuída ao assinante, ele receberá um email solicitando que visite [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) para aproveitar os benefícios da assinatura.  Ao tentar entrar, a assinatura do Visual Studio entrar falhará com um erro que indica que a conta não é reconhecida.  Antes de fazer logon na experiência do [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs), solicite que o assinante siga estas instruções.  Se necessário, você poderá usar este [modelo](#notifying-your-subscribers-using-personal-accounts) para notificar o assinante depois que atribuir uma assinatura.

1. Navegue até https://my.visualstudio.com e clique em **Criar nova conta da Microsoft**.

2. Preencha os campos:
   - Insira o endereço de email que recebeu o Email de Boas-vindas na caixa Someone@example.com
   - Criar a senha
   - Escolher as configurações promocionais
   - Clique em **Avançar**.

3. Conclua as etapas de validação e clique em **Avançar**.

4. Novos usuários talvez precisem concluir o perfil do Visual Studio.

5. A assinatura e os benefícios devem estar visíveis.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Notificar assinantes usando contas pessoais

No cenário descrito acima, o assinante receberá um "Email de Boas-vindas", mas devido ao alias, talvez não consiga entrar.  Você pode usar o texto abaixo para notificar o assinante das etapas acima e recomendar opções de suporte, se necessário.  Substitua %WORD% pelas informações apropriadas para cada assinante.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription, and may have been directed to log into https://my.visualstudio.com based on your Welcome email.  While this is the correct website for consuming benefits, our organization requires you to take a few extra steps before you can access the site.  Please follow the below instructions to help you create a “Microsoft Account” that is tied to our corporate email address.  Once these steps are completed, you will use your email address to access the Subscription benefits.
1. Visit https://my.visualstudio.com

2. Click Create new Microsoft Account on the right hand side

3. Complete the Form:
   - Use your corporate email address in the someone@example.com box
   - Enter a password
   - Select your promotional preference
   - Click Next

4. Complete the account validation steps

5. If necessary, complete the Visual Studio profile

6. You should now see your benefits

Note:  When visiting https://my.visualstudio.com in the future, you may be prompted to select which account you’d like to use (e.g. “Work or School Account” or “Personal Account”).  After following the steps above, you will need to leverage the “Personal Account” option.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```
