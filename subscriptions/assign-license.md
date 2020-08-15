---
title: Atribuir licenças a assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: Saiba como os administradores podem atribuir licenças aos assinantes
ms.openlocfilehash: aa3c219a605b552ea1c4b785ff8fb1f92edf04ac
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249473"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Atribuir licenças no portal de administração de assinaturas do Visual Studio
Como administrador de assinaturas do Visual Studio, você pode usar o portal de administração para atribuir assinaturas a usuários individuais e grupos de usuários.

Para grupos de usuários, você tem opções de como atribuir assinaturas.  
- Você pode atribuir assinaturas uma de cada vez.
- Você também pode carregar rapidamente e facilmente listas de assinantes e suas informações de assinatura usando o recurso de [adição em massa](assign-license-bulk.md) .
- Se sua organização usa o Microsoft Azure Active Directory (AD do Azure), você pode [usar os grupos do Azure ad para atribuir assinaturas](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions) a grupos de usuários.  


## <a name="add-a-single-subscriber"></a>Adicionar um único assinante
Veja como atribuir uma assinatura do Visual Studio a um novo usuário para que eles possam acessar os benefícios da assinatura.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Entre no portal de [Administração](https://manage.visualstudio.com).
2. Para atribuir uma licença a um único assinante do Visual Studio, na parte superior da tabela, selecione **Adicionar**e, em seguida, escolha **assinante individual**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar um único assinante](_img/assign-license-add/add-subscriber-individual.png "Selecione Adicionar e, em seguida, escolha assinante individual para atribuir uma única assinatura.")
3. Insira as informações do novo assinante nos campos do formulário. Se sua organização estiver usando o Azure Active Directory, o campo **Nome** terá uma função de pesquisa para localizar pessoas no diretório atual, permitindo selecionar o usuário correto nos resultados da pesquisa. Quando você selecionar essa pessoa, o email de conexão e o email de notificação serão populados automaticamente.
   > [!div class="mx-imgBorder"]
   > ![Detalhes do assinante](_img/assign-license-add/subscriber-details.png "Insira o nome do assinante e outros detalhes ou escolha um dos membros do locatário.")

    > [!NOTE]
    > Para que os membros de um locatário de Azure Active Directory fiquem visíveis quando você insere um nome de assinante, o administrador deve ser um membro do locatário. 


    Caso deseje que esse assinante tenha acesso a downloads de software quando ele entrar no [Portal de Assinaturas do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), deixe a alternância de downloads habilitada na seção **Configurações de Download**. Se você optar por desabilitar os downloads, o usuário não terá acesso aos downloads de software.  O acesso às chaves do produto também será desabilitado.  O assinante ainda terá acesso a todos os outros benefícios incluídos na assinatura.
   > [!div class="mx-imgBorder"]
   > ! [Acesso a Downloads] (mídia/access-to-downloads.png "escolha" permitir "para fornecer ao Assinante acesso aos downloads de software.")

    Caso deseje adicionar suas próprias anotações de referência para a assinatura, faça isso na seção **Adicionar referência**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar suas próprias anotações de referência a cada assinatura](media/add-subscriber-reference-notes.png "Use o campo de referência para registrar observações sobre esta assinatura.")

    Quando terminar de selecionar as opções e inserir os dados do assinante, escolha **Adicionar** na parte inferior do submenu **Adicionar Assinante**.
   > [!div class="mx-imgBorder"]
   > ![Escolha o botão Adicionar](media/add-button.png "Selecione Adicionar para salvar as informações e atribuir a assinatura ao Assinante.")

## <a name="resend-assignment-emails"></a>Reenviar emails de atribuição
Depois de adicionar um assinante, um email de atribuição será enviado automaticamente para o novo assinante com mais instruções. Você pode enviar o email de atribuição novamente a qualquer momento selecionando o Assinante e, em seguida, selecionando o botão **reenviar** no menu superior.  Para reenviar emails a vários usuários, mantenha pressionada a tecla **Ctrl** enquanto seleciona os assinantes.  Ao selecionar o botão **reenviar** , você verá uma caixa de diálogo solicitando que você confirme se deseja reenviar para esses assinantes.  

## <a name="see-also"></a>Consulte também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Próximas etapas
- Tem muitos usuários para adicionar?  Saiba como atribuir assinaturas a [vários assinantes](assign-license-bulk.md).
- Precisa de ajuda?  Contate o [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).


