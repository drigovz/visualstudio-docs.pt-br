---
title: Entrar em Assinaturas do Visual Studio com sua conta do GitHub | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/09/2020
ms.topic: conceptual
description: Saiba como entrar em suas assinaturas do Visual Studio com sua conta do GitHub.
ms.openlocfilehash: a0a2f69ab3cbab3fdf6c35d9407a59a7c7d49eb1
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78947087"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Entrar em assinaturas do Visual Studio com sua conta do GitHub 

As etapas para entrar na assinatura do Visual Studio dependem do tipo de conta que você está usando. Por exemplo, você pode estar usando uma MSA (conta da Microsoft) ou um endereço de email fornecido pela empresa ou escola. Desde janeiro de 2019 também é possível usar sua conta do GitHub para entrar em algumas assinaturas. 

Este artigo fornecerá as etapas para entrar com sua conta do GitHub.

## <a name="signing-in-with-your-github-account"></a>Entrar com sua conta do GitHub

O suporte a identidade do GitHub permite usar sua conta do GitHub existente como uma credencial para uma conta Microsoft nova ou existente, vinculando sua conta do GitHub à sua conta Microsoft. 

Quando você entra no GitHub, a Microsoft verifica se algum endereço de email associado à sua conta do GitHub corresponde à conta Microsoft pessoal ou corporativa existente. Se o endereço corresponder à sua conta corporativa, será solicitado que você entre nessa conta. Se o endereço corresponder a uma conta pessoal, adicionaremos sua conta do GitHub como um método de conexão para essa conta pessoal.

Depois que suas credenciais de conta Microsoft e do GitHub são vinculadas, você pode usar essa única entrada em qualquer lugar em que uma conta Microsoft pessoal pode ser usada, como nos sites do Azure, nos aplicativos do Office e no Xbox. Essas contas também podem ser usadas para entradas como convidado do Azure Active Directory como uma conta Microsoft, supondo que o endereço de email corresponde àquele no convite.

> [!NOTE]
> Vincular uma identidade do GitHub a uma conta Microsoft não fornece nenhum código de acesso à Microsoft. Quando aplicativos como o Azure DevOps e o Visual Studio exigem acesso aos seus repositórios de código, será solicitado um consentimento específico para esse acesso. 

### <a name="frequently-asked-questions"></a>Perguntas frequentes
As seguintes perguntas frequentes tratam de questões que você poderá encontrar sobre o uso de suas credenciais de conta do GitHub para entrar em assinaturas do Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>P: Esqueci minha senha do GitHub.  Como posso acessar minha conta agora?
A: Você pode recuperar sua conta do GitHub indo para [redefinir sua senha](https://github.com/password_reset). Ou, você pode recuperar sua conta Microsoft vinculada ao GitHub, inserindo o endereço de email da sua conta do GitHub em [Recuperar sua conta](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>P: Eu apaguei minha conta do GitHub.  Como posso acessar minha conta Microsoft (MSA) agora?
R: Se você não tiver nenhuma outra credencial em seu MSA (como uma senha, aplicativo Autenticador ou chave de segurança), você pode recuperar sua conta microsoft usando o endereço de e-mail anexado a ele. Para começar, vá para [Recuperar sua conta](https://account.live.com/password/reset). Você precisará adicionar uma senha à sua conta, de modo que saberemos como conectá-lo mais tarde. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>P: Não há opção "Entrar com o GitHub" na página de login.  Como posso usar minhas credenciais do GitHub para entrar?
A: Digite o endereço de e-mail da conta do GitHub que você escolheu quando criou sua conta Microsoft vinculada ao GitHub. Vamos procurar você e enviá-lo ao GitHub para que possa entrar. Ou, se houver um link de opções de conexão na página de entrada, use o botão **Entrar com o GitHub** que é mostrado depois que você clica nesse link. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>P: Eu não posso fazer login em alguns dos meus aplicativos e produtos com o GitHub.  Por quê?
R: Nem todos os produtos da Microsoft podem acessar GitHub.com a partir de sua página de login — por exemplo, consoles Xbox. Em vez disso, quando você digita o endereço de email da sua conta do GitHub vinculada, enviamos um código para esse endereço para que possamos verificar que realmente é você. Você ainda está entrando na mesma conta, apenas por um método de conexão diferente. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>P: Adicionei uma senha à conta da Microsoft que vinculei à minha conta do GitHub.  Isso causará um problema?
A: De todo. Isso não altera sua senha do GitHub; você terá apenas outra maneira de entrar na sua conta Microsoft. Sempre que você entrar usando seu endereço de email, ofereceremos a opção de entrar com sua senha de conta Microsoft ou acessar o GitHub para entrar. É altamente recomendável que, se precisar adicionar uma senha, você verifique se ela é diferente da senha para sua conta do GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>P: Eu quero adicionar o aplicativo Authenticator à conta que criei usando o GitHub.  Posso fazer isso?
R: Sem problemas — basta baixar o aplicativo e entrar usando seu endereço de e-mail. Quando entrar com seu endereço de email, será solicitado que você escolha o [aplicativo Autenticador](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) ou o GitHub como suas credenciais.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>P: Eu habilitei a autenticação de dois fatores em minhas contas GitHub e Microsoft (MSA), mas quando eu faço login no meu MSA, ainda me pedem para autenticar duas vezes.  Por quê?
R: Devido às restrições de segurança, a Microsoft conta a assinatura com o GitHub como uma verificação de fator único, mesmo que você tenha uma verificação em duas etapas ativada lá. Portanto, você precisará se autenticar novamente na sua conta Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>P: Como posso dizer se minha conta Microsoft e contas do GitHub estão vinculadas?
R: Sempre que você assinar usando o alias da sua conta (endereço de e-mail, número de telefone, nome do Skype), mostraremos todos os métodos de login da sua conta. Se você não vê o GitHub lá, você ainda não o configurou.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>P: Como posso desvincular minhas contas Microsoft e GitHub? 
R: Vá para a [guia Segurança](https://account.microsoft.com/security) de account.microsoft.com e clique em **Mais opções** de segurança para desvincular sua conta do GitHub. Desvincular sua conta do GitHub remove-a como um método de entrada e remove o acesso a todos os repositórios do GitHub no Visual Studio. Outros produtos da Microsoft podem ter solicitado acesso de conta seu GitHub separadamente, então remover o acesso aqui não removerá o acesso em todos os produtos. Vá para a página [permissões de aplicativo](https://github.com/settings/applications) do seu perfil do GitHub para revogar o consentimento dos aplicativos listados lá.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>P: Eu tento usar minha conta do GitHub para fazer login, mas me pediram que eu já tivesse uma identidade Microsoft que eu deveria usar em vez disso.  O que está acontecendo?
R: Se você tiver um endereço de e-mail do Azure Active Directory em sua conta do GitHub, isso significa que você já tem uma identidade Microsoft que pode acessar o Azure e executar pipelines CI usando seu código GitHub. Usar essa conta garante que seus recursos do Azure e os pipelines de build permaneçam dentro de seus limites organizacionais. No entanto, se você estiver fazendo trabalho pessoal, é recomendável colocar um endereço de email pessoal em sua conta do GitHub, de modo que você sempre tenha acesso a ele. Depois de fazer isso, tente entrar novamente e escolha **Usar um endereço de email diferente** quando for solicitado que você entre em sua conta corporativa ou de estudante. Isso permitirá que você crie uma nova conta Microsoft usando esse endereço de email pessoal.

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
Após entrar com êxito no portal de assinaturas, recomendamos acessar a página Benefícios em https://my.visualstudio.com/benefits e explorar as excelentes ferramentas, serviços e ofertas disponíveis para você.  
