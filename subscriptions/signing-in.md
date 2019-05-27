---
title: Entrar em assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 05/14/2019
ms.topic: conceptual
description: Como entrar em sua assinatura do Visual Studio
searchscope: VS Subscription
ms.openlocfilehash: d010a908d28fd6f7be86cee27fa86f0ac24471d6
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805290"
---
# <a name="signing-in-to-your-visual-studio-subscription"></a>Entrando em sua assinatura do Visual Studio

As etapas para entrar na assinatura do Visual Studio dependem do tipo de conta que você está usando.  Por exemplo, você pode estar usando uma MSA (conta da Microsoft) ou um endereço de email fornecido pela empresa ou escola.  Desde janeiro de 2019 também é possível usar sua conta do GitHub para entrar em algumas assinaturas. 

Quatro métodos diferentes de conexão são abordados neste artigo:  Use os links à direita para ir para qualquer uma dessas seções.
1. Entrar com sua MSA (Conta da Microsoft)
2. Entrar com a conta corporativa ou de estudante
3. Usar uma Conta Microsoft para entrar em uma conta corporativa ou de estudante
4. Entrar com sua conta do GitHub

## <a name="signing-in-with-your-microsoft-account-msa"></a>Entrar com sua MSA (Conta da Microsoft)
1. Visite [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Insira o endereço de email fornecido quando você configurou ou adquiriu a assinatura do Visual Studio.

   > [!NOTE]
   > Esse endereço também é identificado no Email de Boas-vindas do assinante que você recebeu ao comprar a assinatura ou inscrever-se no Visual Studio Dev Essentials. Verifique as pastas de lixo eletrônico, se você tiver problemas para localizar o email de boas-vindas.

3. Insira sua senha.
4. Clique em **Entrar**.
5. Neste ponto, a página "Benefícios" deve ser exibida.

### <a name="for-visual-studio-dev-essentials-users"></a>Para usuários do Visual Studio Dev Essentials:
Ao acessar a assinatura do Visual Studio Dev Essentials pela primeira vez, você verá uma caixa de diálogo de boas-vindas.  Clique em **Confirmar** para aceitar os termos e as condições do programa.

## <a name="signing-in-with-your-work-or-school-account"></a>Entrar com sua conta corporativa ou de estudante

1. Visite [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Insira o endereço de email ao qual a nova assinatura do Visual Studio foi atribuída.

   > [!NOTE]
   > Esse endereço também é identificado no Email de Boas-vindas do assinante que você recebeu. Verifique as pastas de lixo eletrônico, se você tiver problemas para localizar o email de boas-vindas.

3. Clique em **Continue**.
4. Você será redirecionado para sua página de entrada empresarial.
5. Insira sua senha.
6. Clique em **Entrar**
7. Neste ponto, a página "Benefícios" deve ser exibida

Agora você pode ver o tipo de assinatura que está usando exibido na barra azul na parte superior do portal.

Você também pode ver a assinatura atualmente selecionada no canto superior direito, sob o nome de usuário.  Ele dirá "Mostrando:", seguido da assinatura.  Se tiver mais de uma assinatura, você poderá clique na seta suspensa e selecionar a assinatura que deseja usar.

## <a name="using-your-microsoft-account-to-sign-in-to-a-work-or-school-account"></a>Usar a Conta da Microsoft para entrar em uma conta corporativa ou de estudante

1. Acesse [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
2. Insira o endereço de email ao qual a nova assinatura do Visual Studio foi atribuída

   > [!NOTE]
   > Esse endereço também é identificado na Carta de Boas-vindas do assinante. Se você não recebeu a Carta de boas-vindas, verifique as pastas de lixo eletrônico

3. Clique em **Continue**.
4. Você será redirecionado para uma página de decisão.
    - Selecione **Conta corporativa ou de estudante** se a assinatura estiver atribuída a uma conta "Corporativa ou de estudante" associada a um locatário do AAD (Azure Active Directory).
    - Selecione **Pessoal** se a assinatura estiver associada a um endereço de email "Corporativo", mas também tiver sido convertida em uma MSA (Conta da Microsoft) "Pessoal".

        > [!NOTE]
        > Esse será o caso para vários assinantes que usaram as assinaturas do Visual Studio (anteriormente, MSDN) no passado.

    - Se um caminho falhar, tente o outro.  Administradores de assinatura podem ter modificado a assinatura.

5. Insira sua senha.
6. Clique em **Entrar**.
7. Neste ponto, a página "Benefícios" deve ser exibida.

## <a name="signing-in-with-your-github-account"></a>Entrar com sua conta do GitHub

O suporte a identidade do GitHub permite usar sua conta do GitHub existente como uma credencial para uma conta Microsoft nova ou existente, vinculando sua conta do GitHub à sua conta Microsoft. 

Quando você entra no GitHub, a Microsoft verifica se algum endereço de email associado à sua conta do GitHub corresponde à conta Microsoft pessoal ou corporativa existente. Se o endereço corresponder à sua conta corporativa, será solicitado que você entre nessa conta. Se o endereço corresponder a uma conta pessoal, adicionaremos sua conta do GitHub como um método de conexão para essa conta pessoal.

Depois que suas credenciais de conta Microsoft e do GitHub são vinculadas, você pode usar essa única entrada em qualquer lugar em que uma conta Microsoft pessoal pode ser usada, como nos sites do Azure, nos aplicativos do Office e no Xbox. Essas contas também podem ser usadas para entradas como convidado do Azure Active Directory como uma conta Microsoft, supondo que o endereço de email corresponde àquele no convite.

> [!NOTE]
> Vincular uma identidade do GitHub a uma conta Microsoft não fornece nenhum código de acesso à Microsoft. Quando aplicativos como o Azure DevOps e o Visual Studio exigem acesso aos seus repositórios de código, será solicitado um consentimento específico para esse acesso. 

### <a name="frequently-asked-questions"></a>Perguntas frequentes
As seguintes perguntas frequentes tratam de questões que você poderá encontrar sobre o uso de suas credenciais de conta do GitHub para entrar em assinaturas do Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>P: Esqueci minha senha do GitHub.  Como posso acessar minha conta agora?
R:  Você pode recuperar sua conta do GitHub acessando [Redefinir sua senha](https://github.com/password_reset). Ou, você pode recuperar sua conta Microsoft vinculada ao GitHub, inserindo o endereço de email da sua conta do GitHub em [Recuperar sua conta](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>P: Excluí minha conta do GitHub.  Como posso acessar minha conta Microsoft (MSA) agora?
R: Se não tiver outras credenciais em sua MSA (como uma senha, um aplicativo autenticador ou uma chave de segurança), você poderá recuperar sua conta Microsoft usando o endereço de email anexado a ela. Para começar, vá para [Recuperar sua conta](https://account.live.com/password/reset). Você precisará adicionar uma senha à sua conta, de modo que saberemos como conectá-lo mais tarde. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>P: Não há nenhuma opção "Entrar com o GitHub" na página de entrada.  Como posso usar minhas credenciais do GitHub para entrar?
R:  Digite o endereço de email da conta do GitHub que você escolheu ao criar sua conta Microsoft vinculada ao GitHub. Vamos procurar você e enviá-lo ao GitHub para que possa entrar. Ou, se houver um link de opções de conexão na página de entrada, use o botão **Entrar com o GitHub** que é mostrado depois que você clica nesse link. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>P: Não consigo entrar para alguns dos meus aplicativos e produtos com o GitHub.  Por quê?
R:  Nem todos os produtos da Microsoft podem acessar o GitHub.com das respectivas páginas de entrada, por exemplo, os consoles Xbox. Em vez disso, quando você digita o endereço de email da sua conta do GitHub vinculada, enviamos um código para esse endereço para que possamos verificar que realmente é você. Você ainda está entrando na mesma conta, apenas por um método de conexão diferente. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>P:  Eu adicionei uma senha para a conta Microsoft que vinculei à minha conta do GitHub.  Isso causará um problema?
R:  De forma alguma. Isso não altera sua senha do GitHub; você terá apenas outra maneira de entrar na sua conta Microsoft. Sempre que você entrar usando seu endereço de email, ofereceremos a opção de entrar com sua senha de conta Microsoft ou acessar o GitHub para entrar. É altamente recomendável que, se precisar adicionar uma senha, você verifique se ela é diferente da senha para sua conta do GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>P: Quero adicionar o aplicativo Autenticador para a conta que criei usando o GitHub.  Posso fazer isso?
R:  Sem problemas – basta baixar o aplicativo e entrar usando seu endereço de email. Quando entrar com seu endereço de email, será solicitado que você escolha o [aplicativo Autenticador](https://go.microsoft.com/fwlink/?linkid=2090219) ou o GitHub como suas credenciais.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>P: Habilitei a autenticação de dois fatores em ambas as minhas contas do GitHub e da Microsoft (MSA), mas quando eu entro na minha MSA, ainda assim é solicitado que eu me autentique duas vezes.  Por quê?
R: Devido a restrições de segurança, a Microsoft considera a entrada com o GitHub como uma verificação de fator único, mesmo se você tem a verificação em duas etapas habilitada. Portanto, você precisará se autenticar novamente na sua conta Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>P:  Como saber se minha conta Microsoft e contas do GitHub estão vinculadas?
R:  Sempre que você entrar usando seu alias de conta (endereço de email, número de telefone, nome do Skype), mostraremos todos os métodos de conexão para sua conta. Se você não vê o GitHub lá, você ainda não o configurou.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>P:  Como desvincular minhas contas Microsoft e do GitHub? 
R:  Vá para a [Guia de segurança](https://account.microsoft.com/security) de account.microsoft.com e clique em **Mais opções de segurança** para desvincular sua conta do GitHub. Desvincular sua conta do GitHub remove-a como um método de entrada e remove o acesso a todos os repositórios do GitHub no Visual Studio. Outros produtos da Microsoft podem ter solicitado acesso de conta seu GitHub separadamente, então remover o acesso aqui não removerá o acesso em todos os produtos. Vá para a página [permissões de aplicativo](https://github.com/settings/applications) do seu perfil do GitHub para revogar o consentimento dos aplicativos listados lá.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>P:  Eu tento usar minha conta do GitHub para entrar, mas é avisado que eu já tenho uma identidade da Microsoft e que devo usá-la em vez disso.  O que está acontecendo?
R:  Se você tem um endereço de email do Azure Active Directory em sua conta do GitHub, isso significa que você já tem uma identidade da Microsoft que pode acessar o Azure e executar pipelines de CI usando seu código do GitHub. Usar essa conta garante que seus recursos do Azure e os pipelines de build permaneçam dentro de seus limites organizacionais. No entanto, se você estiver fazendo trabalho pessoal, é recomendável colocar um endereço de email pessoal em sua conta do GitHub, de modo que você sempre tenha acesso a ele. Depois de fazer isso, tente entrar novamente e escolha **Usar um endereço de email diferente** quando for solicitado que você entre em sua conta corporativa ou de estudante. Isso permitirá que você crie uma nova conta Microsoft usando esse endereço de email pessoal.
