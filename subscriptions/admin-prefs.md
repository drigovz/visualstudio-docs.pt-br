---
title: Definir preferências de contrato no Portal de Administração
author: evanwindom
ms.author: lank
manager: lank
ms.date: 08/21/2019
ms.topic: conceptual
description: Saiba como definir preferências de idioma, contatos, nível de assinatura e outros no Portal de Administração
ms.openlocfilehash: 24e9ddfa92ee63e4d15eea086224e1069d4bcbc8
ms.sourcegitcommit: c90a998716b3dfa614dedc61a1bea515364efbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000976"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Definir preferências para os contratos no Portal de Administração
Os superadministradores agora podem definir algumas preferências no Portal de Administração que serão aplicadas globalmente para cada contrato.  Essas preferências determinarão o que os administradores dos contratos poderão definir quando adicionarem assinantes e só podem ser modificadas globalmente por superadministradores.  

## <a name="access-preferences"></a>Preferências de acesso
Você precisa estar conectado ao [portal de administração](https://manage.visualstudio.com) usando uma ID de entrada que tenha direitos de superadministrador no contrato para exibir ou modificar as preferências.  

Para definir suas preferências:
1. Entre no portal de administração com uma ID que tenha privilégios de superadministrador.
2. Clique na guia **Gerenciar Administradores**.
   > [!div class="mx-imgBorder"]
   > ![Botão Preferências de Administrador](_img/admin-prefs/admin-prefs-button.png)

3. Clique em **Preferências de Contrato**.
Um painel será aberto à direita e as preferências disponíveis serão exibidas. 

   > [!div class="mx-imgBorder"]
   > ![Caixa de diálogo de submenu Preferências de Administrador](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>Definir suas preferências
Vamos explorar cada uma das preferências disponíveis e seus efeitos. 

### <a name="agreement"></a>Contrato
Caso você tenha vários contratos para os quais você seja superadministrador, poderá escolher o contrato desejado na lista suspensa.  As preferências definidas serão aplicadas somente a esse contrato.  Os administradores individuais podem substituir algumas dessas preferências, conforme o caso, ao atribuir assinaturas. 

Se houver apenas um contrato associado ao endereço de email que você usou para entrar, ele será exibido e a lista suspensa será desabilitada. 

### <a name="contact-email-address"></a>Endereço de email de contato
Essas preferências fornecem uma maneira de os assinantes contatarem os administradores por meio do uso do botão **Contatar meu Administrador** na [página de assinaturas](https://my.visualstudio.com/subscriptions) do portal do assinante.  Se essa preferência for deixada em branco, as mensagens do assinante serão encaminhadas para todos os administradores e os superadministradores do contrato.  Recomendamos o uso de um alias de email de grupo ou um grupo de segurança para adaptar o público-alvo a esse email de contato. Você também poderá optar por inserir o endereço de email de um indivíduo, se preferir.

> [!NOTE]
> O endereço de email listado aqui NÃO será fornecido aos assinantes.  Quando um assinante enviar uma solicitação **Contatar meu Administrador** no portal do assinante, a mensagem será encaminhada para o alias sem expô-la aos assinantes. 

### <a name="default-external-subscribers-setting"></a>Configuração padrão de assinantes externos
Essa preferência permite que você decida se os administradores podem adicionar assinantes de fora do diretório/locatário da organização.  Se você desligar essa opção, nenhum assinante externo será permitido.  Se você habilitá-la e um administrador tentar adicionar um assinante externo, ele deverá confirmar sua escolha e terá permissão para atribuir a assinatura. Os administradores não podem substituir essa configuração. 

### <a name="default-downloads-setting"></a>Configuração padrão de downloads
A habilitação dessa configuração, que está ativada por padrão, permitirá que os assinantes acessem os downloads quando os administradores criarem assinaturas.  Os administradores ainda podem desabilitar os downloads para cada assinatura individual.  

### <a name="default-subscription-level"></a>Nível de assinatura padrão
Use essa configuração para determinar qual dos níveis de assinatura incluídos no contrato é selecionado por padrão quando uma assinatura é atribuída a um usuário.  Os administradores podem alterar a configuração para qualquer nível de assinatura no contrato – isso apenas impede que você precise repetidamente fazer a escolha mais comum. 

### <a name="default-communication-preferences"></a>Opções de comunicação padrão
A definição de uma localidade e um idioma de comunicação padrão pode simplificar o processo de atribuição de assinaturas.  Por exemplo, caso sua equipe de desenvolvimento esteja localizada em um país diferente daquele da equipe de administração, você poderá definir as preferências mais adequadas à localização dos assinantes. Essas configurações ainda podem ser alteradas por todos os administradores para assinantes individuais. 

## <a name="frequently-asked-questions"></a>Perguntas frequentes
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>P:  Posso desabilitar o **Endereço de email de contato** de modo que os assinantes não possam contatar os administradores?
R:  Não. Embora você possa determinar quais administradores são contatados usando um grupo de segurança, um alias de email de grupo ou um endereço de email individual, o recurso não pode ser desabilitado.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>P: Se eu responder ao email de um assinante, ele terá meu endereço de email?
R:  Como sua resposta virá de qualquer cliente de email que você esteja usando, a resposta que o assinante receberá mostrará o endereço de email que está sendo usado.  Portanto, se você estiver respondendo com um alias de grupo, ele verá o alias de grupo.  Se você responder com seu próprio endereço de email, ele verá isso.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>P: Onde posso saber mais sobre o recurso **Contatar meu Administrador** no portal do assinante?
R:  Confira nosso artigo [Contatar meu Administrador](contact-my-admin.md). 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>P: Se não preenchermos o **Endereço de email de contato** e um assinante usar o recurso **Contatar meu Administrador**, quem receberá a solicitação?
R:  Se nenhum endereço de email específico for definido na preferência de **Endereço de email de contato**, todos os administradores do contrato receberão a solicitação. 

## <a name="resources"></a>Recursos
- [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="next-steps"></a>Próximas etapas
- Saiba como [atribuir assinaturas](assign-license.md)
- Saiba mais sobre a gama completa de [benefícios da assinatura](https://visualstudio.microsoft.com/vs/benefits/)

