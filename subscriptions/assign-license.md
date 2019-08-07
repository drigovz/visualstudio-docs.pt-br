---
title: Atribuir licenças a assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Saiba como os administradores podem atribuir licenças aos assinantes
ms.openlocfilehash: 8125c5cbad2ff44dabbf1b0c5014c313d75d2e71
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604722"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Atribuir licenças no portal de administração de assinaturas do Visual Studio
Como administrador de assinaturas do Visual Studio, você pode usar o portal de administração para atribuir assinaturas a usuários individuais e grupos de usuários.

Para grupos de usuários, você pode atribuir assinaturas a eles uma de cada vez ou usar o recurso [Adição em Massa](assign-license-bulk.md) para carregar listas de assinantes e suas informações de assinatura de forma rápida e fácil.

## <a name="add-a-single-subscriber"></a>Adicionar um único assinante
Veja a seguir como atribuir uma licença de assinatura do Visual Studio a um novo usuário para que ele possa acessar os benefícios da assinatura.

1. Entre no [portal de administração](https://manage.visualstudio.com).
2. Para atribuir uma licença a único assinante do Visual Studio, na parte superior da tabela, selecione **Adicionar**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar um único assinante](media/add-single-subscriber.png)
3. Insira as informações do novo assinante nos campos do formulário. Se sua organização estiver usando o Azure Active Directory, o campo **Nome** terá uma função de pesquisa para localizar pessoas no diretório atual, permitindo selecionar o usuário correto nos resultados da pesquisa. Quando você selecionar essa pessoa, o email de conexão e o email de notificação serão populados automaticamente.
   > [!div class="mx-imgBorder"]
   > ![Detalhes do assinante](_img/assign-license-add/subscriber-details.png)

    Caso deseje que esse assinante tenha acesso a downloads de software quando ele entrar no [Portal de Assinaturas do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), deixe a alternância de downloads habilitada na seção **Configurações de Download**. Se optar por desabilitar downloads, o usuário não terá acesso aos downloads de software, mas ainda terá acesso a todos os outros benefícios incluídos na assinatura.
   > [!div class="mx-imgBorder"]
   > ![Acesso aos downloads](media/access-to-downloads.png)

       If you'd like to add your own reference notes to the subscription, you can do so in the **Add reference** section.
   > [!div class="mx-imgBorder"]
   > ![Adicionar suas próprias anotações de referência a cada assinatura](media/add-subscriber-reference-notes.png)

    Quando terminar de selecionar as opções e inserir os dados do assinante, escolha **Adicionar** na parte inferior do submenu **Adicionar Assinante**.
   > [!div class="mx-imgBorder"]
   > ![Escolher o botão Adicionar](media/add-button.png)

4. Depois que você adicionar o assinante, um Email de Atribuição será enviado automaticamente para o novo assinante com mais instruções. É possível enviar o Email de atribuição novamente a qualquer momento selecionando o assinante e clicando no botão **Reenviar** no menu superior.

## <a name="next-steps"></a>Próximas etapas
- Tem muitos usuários para adicionar?  Saiba como atribuir assinaturas a [vários assinantes](assign-license-bulk.md).
- Precisa de ajuda?  Contate o [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

