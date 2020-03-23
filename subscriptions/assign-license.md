---
title: Atribuir licenças a assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Saiba como os administradores podem atribuir licenças aos assinantes
ms.openlocfilehash: 3d444f930d1fab166d437911b5609caf75cad09e
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78263299"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Atribuir licenças no portal de administração de assinaturas do Visual Studio
Como administrador de assinaturas do Visual Studio, você pode usar o portal de administração para atribuir assinaturas a usuários individuais e grupos de usuários.

Para grupos de usuários, você tem opções de como atribuir assinaturas.  
- Você pode atribuir assinaturas uma de cada vez.
- Você também pode enviar de forma rápida e fácil listas de assinantes e suas informações de assinatura usando o recurso [Bulk add.](assign-license-bulk.md)
- Se sua organização usar o Microsoft Azure Active Directory (Azure AD), você pode usar grupos AD do Azure para atribuir assinaturas a grupos de usuários.  (Esse recurso está sendo implantado em fases e pode não estar disponível imediatamente para sua organização.)


## <a name="add-a-single-subscriber"></a>Adicionar um único assinante
Veja como atribuir uma assinatura do Visual Studio a um novo usuário para que ele possa acessar os benefícios da assinatura.

1. Faça login no portal de [administração.](https://manage.visualstudio.com)
2. Para atribuir uma licença a um único assinante do Visual Studio, no topo da tabela, **selecione Adicionar**, em seguida, escolha **Assinante Individual**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar um único assinante](_img/assign-license-add/add-subscriber-individual.png)
3. Insira as informações do novo assinante nos campos do formulário. Se sua organização estiver usando o Azure Active Directory, o campo **Nome** terá uma função de pesquisa para localizar pessoas no diretório atual, permitindo selecionar o usuário correto nos resultados da pesquisa. Quando você selecionar essa pessoa, o email de conexão e o email de notificação serão populados automaticamente.
   > [!div class="mx-imgBorder"]
   > ![Detalhes do assinante](_img/assign-license-add/subscriber-details.png)

    Caso deseje que esse assinante tenha acesso a downloads de software quando ele entrar no [Portal de Assinaturas do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), deixe a alternância de downloads habilitada na seção **Configurações de Download**. Se optar por desabilitar downloads, o usuário não terá acesso aos downloads de software, mas ainda terá acesso a todos os outros benefícios incluídos na assinatura.
   > [!div class="mx-imgBorder"]
   > ![Acesso aos downloads](media/access-to-downloads.png)

    Caso deseje adicionar suas próprias anotações de referência para a assinatura, faça isso na seção **Adicionar referência**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar suas próprias anotações de referência a cada assinatura](media/add-subscriber-reference-notes.png)

    Quando terminar de selecionar as opções e inserir os dados do assinante, escolha **Adicionar** na parte inferior do submenu **Adicionar Assinante**.
   > [!div class="mx-imgBorder"]
   > ![Escolher o botão Adicionar](media/add-button.png)

## <a name="resend-assignment-emails"></a>Reenviar e-mails de atribuição
Depois de adicionar um assinante, um e-mail de atribuição será enviado automaticamente ao novo assinante com instruções adicionais. Você pode enviar o e-mail de atribuição novamente a qualquer momento, selecionando o assinante e clicando no botão **Reenviar** no menu superior.  Para reenviar e-mails para vários usuários, mantenha a tecla **Ctrl** enquanto seleciona os assinantes.  Quando você clica no botão **Reenviar,** você verá um diálogo pedindo que você confirme que deseja reenviar para esses assinantes.  

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Próximas etapas
- Tem muitos usuários para adicionar?  Saiba como atribuir assinaturas a [vários assinantes](assign-license-bulk.md).
- Precisa de ajuda?  Contate o [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).


