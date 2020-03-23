---
title: A entrada nas assinaturas do Visual Studio pode falhar ao usar aliases | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: A entrada poderá falhar se forem usados aliases ou nomes amigáveis
ms.openlocfilehash: 0f5ed4fe67dbd863a7ba4c22f10946cbeb1c36b0
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509051"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>A assinatura em assinaturas do Visual Studio pode falhar ao usar pseudônimos
Dependendo do tipo de conta usada para fazer login, as assinaturas disponíveis [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)podem não ser exibidas corretamente ao fazer login. Uma possível causa é o uso de "alias" ou "nomes amigáveis" em vez da identidade à qual a assinatura foi atribuída. Isso é chamado de "alias".

## <a name="what-is-aliasing"></a>O que é um alias?
O termo "alias" refere-se a usuários com identidades diferentes para entrar no Windows (ou no Active Directory) e para acessar o email.

Os aliases podem ser encontrados quando uma empresa tem um Serviço Online da Microsoft para a entrada no diretório, como ‘JohnD@contoso.com’, mas os usuários acessam as contas de email usando aliases ou nomes amigáveis, como ‘John.Doe@contoso.com’. Certifique-se de que seus usuários estão usando o "Endereço de e-mail de login" conforme listado no https://manage.visualstudio.com portal de admin para acessar suas assinaturas. 

## <a name="what-are-the-potential-issues"></a>Quais são os problemas potenciais?

Dependendo do tipo de conta do assinante, ele pode encontrar um dos dois problemas. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problema de incompatibilidade de trabalho ou conta escolar UPN 
Uma incompatibilidade upn pode ser encontrada quando uma empresa tem um Diretório Ativo configurado onde o UserPrincipalName (UPN) não é o mesmo que o Endereço SMTP primário. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Como detectar se seu endereço de login é afetado por uma incompatibilidade upn 

1. Faça https://my.visualstudio.com/subscriptions login usando o endereço de login mencionado no seu e-mail de atribuição de assinatura.

2. Verifique se o endereço de e-mail de login listado no canto superior direito da página corresponde ao endereço que você usou para fazer login.  Se isso não acontecer, sua UPN é incompatível e você não poderá visualizar sua assinatura. 

> [!div class="mx-imgBorder"]
> ![Faça login no endereço de e-mail](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Como corrigir uma incompatibilidade upn

1. Acesse o portal de Gestão de Administração do Estúdio Visual[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Localize o assinante com a questão da incompatibilidade upn. (O recurso [Filtro](search-license.md) pode facilitar a encontrar um assinante.)

3. Altere o endereço de e-mail de login para upn do assinante 

0. Salvar as alterações 

0. Informe o assinante para sair do portal do assinante e acessar novamente através da UPN 

### <a name="personal-account-aliasing-issue"></a>Problema de aliasing de conta pessoal

As contas de assinatura pessoal também podem sofrer problemas se o endereço de e-mail usado para entrar no portal De assinaturas do Visual Studio não corresponder ao endereço de e-mail associado à assinatura. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Como detectar se sua conta de assinatura pessoal é impactada por um problema de aliasing

1. Faça login em[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Verifique se o endereço de e-mail de login listado no canto superior direito da página corresponde ao endereço que você usou para fazer login.  Se o endereço de e-mail inscrito não for o mesmo que o endereço de e-mail usado para acessar o site, há um conflito entre sua conta e o alias.

#### <a name="how-to-fix-an-alias-issue"></a>Como corrigir um problema de alias

A plataforma Visual Studio prioriza o alias principal para mostrar detalhes da assinatura. 

1. Vá para **Gerenciar como você faz login na Microsoft**. Faça login na sua conta da Microsoft, se solicitado. 

2. Em Aliases de conta, selecione **Fazer principal** ao lado do endereço de e-mail usado para atribuir a assinatura. 

> [!div class="mx-imgBorder"]
> ![Defina o endereço de e-mail principal](_img//aliasing/account-aliases.png)

3. Sair do portal de assinaturas do Visual Studio (https://my.visualstudio.com) 

4. Faça login usando a conta usada para atribuir a assinatura que agora deve ser configurada como alias principal. 

## <a name="preventing-aliasing-issues"></a>Prevenção de problemas de aliasing

Como administrador, há duas opções para garantir que seus assinantes [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)tenham uma experiência de login bem-sucedida em .
- A primeira opção (recomendada), é aproveitar a conta do diretório como o login https://my.visualstudio.compara o portal De Assinaturas do Visual Studio em .  
- A segunda opção (menos segura), é permitir que seus assinantes entrem usando um endereço de e-mail diferente do endereço de e-mail do diretório.

Ambas as opções estão configuradas no portal de admin completando as seguintes etapas:  
1. Inscreva-se em[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Se você estiver alterando um único usuário, selecione esse usuário na tabela e clique com o botão direito do mouse para editar. Isso abrirá um painel onde você pode modificar o endereço de e-mail de login. Faça as atualizações necessárias no campo de endereço de e-mail de login. Clique em salvar e as alterações entrarão em vigor.  

0. Se você precisar fazer essas alterações em uma grande quantidade de usuários, você pode utilizar o recurso de edição em massa. Leia a [Edição de vários assinantes usando](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) artigo de edição em massa para obter mais informações.

> [!NOTE]
> Para alterações individuais e em massa, os assinantes receberão um e-mail com instruções de que seu endereço de e-mail de login foi alterado e eles precisarão fazer login usando o endereço de e-mail atualizado. Também é importante notar que se o assinante ativou anteriormente os benefícios o outro endereço de login, ele precisará continuar usando o outro endereço de login para acessá-los.  

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Próximas etapas
Saiba mais sobre como gerenciar assinaturas do Visual Studio.
- [Atribuir assinaturas individuais](assign-license.md)
- [Atribuir várias assinaturas](assign-license-bulk.md)
- [Editar assinaturas](edit-license.md)
- [Determine o uso máximo](maximum-usage.md)


