---
title: A entrada nas assinaturas do Visual Studio pode falhar ao usar aliases | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: A entrada poderá falhar se forem usados aliases ou nomes amigáveis
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276627"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>A entrada nas assinaturas do Visual Studio poderá falhar ao usar aliases
Dependendo do tipo de conta usado para entrar, é possível que as assinaturas disponíveis não sejam exibidas corretamente ao entrar no [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Uma possível causa é o uso de "alias" ou "nomes amigáveis" em vez da identidade à qual a assinatura foi atribuída. Isso é chamado de "alias".

## <a name="what-is-aliasing"></a>O que é um alias?
O termo "alias" refere-se a usuários com identidades diferentes para entrar no Windows (ou no Active Directory) e para acessar o email.

Os aliases podem ser encontrados quando uma empresa tem um Serviço Online da Microsoft para a entrada no diretório, como ‘olivia@contoso.com’, mas os usuários acessam as contas de email usando aliases ou nomes amigáveis, como ‘OliviaG@contoso.com’. Verifique se os usuários estão se conectando usando o "endereço de email de entrada", conforme listado no portal de administração de assinaturas do Visual Studio em https://manage.visualstudio.com para acessar suas assinaturas

## <a name="as-an-administrator-what-options-do-i-have"></a>Como administrador, quais opções tenho?

Dependendo do tipo de conta do Assinante, localize a solução aplicável abaixo:

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problema de incompatibilidade de UPN da conta corporativa ou de estudante

Uma incompatibilidade de UPN (nome principal do usuário) pode ser encontrada quando um compnay tem um Directory ativo configurado onde o UPN não é o mesmo que o endereço SMTP primário. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Como detectar se o endereço de entrada de um usuário tem uma incompatibilidade de UPN

Faça o usuário concluir as seguintes etapas:

1. Entre no https://my.visualstudio.com usando o endereço de entrada mencionado em seu email de atribuição de assinatura.  

    > [!NOTE]
    > Se eles não tiverem seu email de atribuição de assinatura, você poderá reenviá-lo a eles de dentro do portal de administração.  

2. Clique na guia **Assinaturas**.
3. Verifique se o endereço de email exibido no canto superior direito, onde diz "você está conectado como..." é o mesmo que o endereço de email de entrada em seu email de atribuição de assinatura.  Se não estiver, eles não poderão acessar seus benefícios de assinatura. 

   > [!div class="mx-imgBorder"]
   > página de assinaturas do ![](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>Como corrigir a incompatibilidade de UPN

1. Acesse o portal de gerenciamento da administração do Visual Studio em https://manage.visualstudio.com 

2. Localize o usuário que tem o problema de incompatibilidade de UPN.  O recurso de [filtro](search-license.md) pode facilitar essa tarefa se você tiver muitas assinaturas. 

3. Altere o endereço de email de entrada para o UPN do usuário.

4. Salvar as alterações 

5. Peça ao usuário para fazer logoff do portal do assinante e entrar novamente usando o UPN.   

### <a name="personal-account-aliasing-issue"></a>Problema de alias de conta pessoal

Problemas de alias também podem afetar contas pessoais. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Como detectar se uma conta pessoal tem um problema de alias

1. https://my.visualstudio.comde entrada.

2. Clique na guia **assinaturas** e verifique o endereço com o qual você está conectado. 

3. Se o endereço de email conectado não for o mesmo que o endereço de email usado para acessar o site, haverá um conflito entre sua conta e o alias. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Como corrigir um problema de alias de conta pessoal

A plataforma de assinaturas do Visual Studio prioriza o alias principal para mostrar os detalhes da assinatura.  Para resolver o problema, você precisa fazer um alias de email diferente de seu alias principal para entrar. 

1. Vá para [gerenciar como entrar na Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842796).
2. Entre em seu conta Microsoft, se solicitado. 
3. Em aliases de conta, selecione **tornar primário** ao lado do endereço de email usado para atribuir a assinatura. 
4. Em aliases de conta, selecione tornar primário ao lado do endereço de email usado para atribuir a assinatura. 
5. Saia do portal de assinante do Visual Studio (https://my.visualstudio.com) 
6. Acesse o portal novamente usando o novo alias primário. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Garantir uma experiência bem-sucedida para seus usuários

Como administrador, há duas opções para garantir que seus assinantes tenham uma experiência de entrada bem-sucedida em https://my.visualstudio.com. 

- A primeira opção (recomendado) é aproveitar a conta do diretório como o endereço de entrada em https://manage.visualstudio.com.
- A segunda opção, que é menos segura, a segunda opção (menos segura) é permitir que seus assinantes entrem usando um endereço de email diferente do seu endereço de email do diretório.

Ambas as opções são configuradas no portal de administração ao concluir as seguintes etapas:

1. Entrar https://manage.visualstudio.com 

2. Se você estiver alterando um único usuário, selecione esse usuário na tabela e clique com o botão direito do mouse para editar. Isso abrirá um painel em que você pode modificar o endereço de email de entrada.  

3. Faça as atualizações necessárias no campo endereço de email de entrada. 

4. Clique em salvar e as alterações entrarão em vigor.  
Se você precisar fazer essas alterações em uma grande quantidade de usuários, poderá utilizar o recurso de edição em massa. Leia a seção **Editar vários assinantes usando edição em massa** do nosso artigo [editar assinaturas]] (edit-License.MD) para obter mais informações sobre esse processo.  

## <a name="next-steps"></a>Próximas etapas
Saiba mais sobre como gerenciar assinaturas do Visual Studio.
- [Atribuir assinaturas individuais](assign-license.md)
- [Atribuir várias assinaturas](assign-license-bulk.md)
- [Editar assinaturas](edit-license.md)
- [Excluir assinaturas](delete-license.md)
- [Determinar o uso máximo](maximum-usage.md)

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](/visualstudio/)
- [Documentação do Azure DevOps](/azure/devops/)
- [Documentação do Azure](/azure/)
- [Documentação do Microsoft 365](/microsoft-365/)
