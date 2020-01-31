---
title: Atribuir licenças a assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Saiba como os administradores podem atribuir licenças aos assinantes
ms.openlocfilehash: 4ebec96f488a480ccd9b96387f2656aadd6ba2f9
ms.sourcegitcommit: 6375001ab26786af8d4d449f5846f8a49779ed18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76892175"
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

    Caso deseje adicionar suas próprias anotações de referência para a assinatura, faça isso na seção **Adicionar referência**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar suas próprias anotações de referência a cada assinatura](media/add-subscriber-reference-notes.png)

    Quando terminar de selecionar as opções e inserir os dados do assinante, escolha **Adicionar** na parte inferior do submenu **Adicionar Assinante**.
   > [!div class="mx-imgBorder"]
   > ![Escolher o botão Adicionar](media/add-button.png)

## <a name="resend-assignment-emails"></a>Reenviar emails de atribuição
Depois de adicionar um assinante, um email de atribuição será enviado automaticamente para o novo assinante com mais instruções. Você pode enviar o email de atribuição novamente a qualquer momento selecionando o Assinante e clicando no botão **reenviar** no menu superior.  Para reenviar emails a vários usuários, mantenha pressionada a tecla **Ctrl** enquanto seleciona os assinantes.  Ao clicar no botão **reenviar** , você verá uma caixa de diálogo solicitando que você confirme que deseja reenviar para esses assinantes.  

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}
- Tem muitos usuários para adicionar?  Saiba como atribuir assinaturas a [vários assinantes](assign-license-bulk.md).
- Precisa de ajuda?  Contate o [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

