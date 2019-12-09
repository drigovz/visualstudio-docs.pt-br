---
title: Atribuir licenças a grupos de usuários para assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Saiba como os administradores podem atribuir licenças a vários assinantes
ms.openlocfilehash: 7d54dcf3cf3e7fea7845a4e9a0053de4ba734ae9
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68610516"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Atribuir assinaturas a vários usuários
O portal de administração de assinaturas permite que você adicione usuários individualmente ou em grupos grandes.  Para adicionar usuários únicos, confira [Adicionar usuários únicos](assign-license.md).

## <a name="use-bulk-add-to-assign-subscriptions"></a>Usar Adição em Massa para atribuir assinaturas
1. Entre no portal de administração de assinaturas do Visual Studio em https://manage.visualstudio.com.
2. Para adicionar vários assinantes de uma vez, navegue para a guia **Gerenciar Assinantes**. Na faixa de opções na parte superior, clique em **Adição em Massa**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar vários assinantes](media/add-multiple-subscribers.png)

2. A Adição em Massa usa um modelo do Microsoft Excel para carregar informações dos assinantes. Na caixa de diálogo Carregar Vários Assinantes, clique em **Baixar** para baixar o modelo.
   > [!div class="mx-imgBorder"]
   > ![Baixar o modelo do Excel para carregar vários assinantes](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Sempre baixe a versão mais recente deste modelo. Se você usar uma versão mais antiga, o upload em massa poderá falhar.

3. Na planilha do Excel, preencha os campos com as informações dos indivíduos aos quais deseja atribuir assinaturas. (*Referência* é um campo opcional.) Salve o arquivo localmente depois que terminar.

   Para que não haja problemas com o upload, observe as seguintes melhores práticas:

    - Verifique se nenhum dos campos do formulário contém vírgulas.
    - Remova os espaços antes e depois de campos de formulário.
    - Verifique se os nomes do usuário não contêm espaços extras entre nomes ou sobrenomes de duas partes (por exemplo, se uma pessoa tiver um nome de duas partes, como "Maria Eduarda", ele deverá ser digitado como "MariaEduarda", porque o sistema não cortará o espaço extra).

4. Retorne ao portal de Administração de Assinaturas do Visual Studio. Na caixa de diálogo **Carregar Vários Assinantes**, clique em **Procurar**.
   > [!div class="mx-imgBorder"]
   > ![Navegar para o modelo salvo para carregar vários assinantes](media/bulk-add-browse-saved-template.png)

5. Navegue para o arquivo do Excel que você salvou e, em seguida, clique em **OK**.
   > [!div class="mx-imgBorder"]
   > ![Carregar o modelo do Excel para carregar vários assinantes](media/bulk-upload-subscribers.png)

    Uma caixa de diálogo de progresso do upload será exibida.

    Se o modelo contiver erros, o upload falhará e os erros serão mostrados para que você possa corrigir o modelo e tentar o upload em massa novamente.
   > [!div class="mx-imgBorder"]
   > ![Mensagem de erro em caso de falha no upload de vários assinantes](media/bulk-add-template-failed.png)

    Quando o upload for bem-sucedido, você verá a lista de assinantes e uma mensagem de confirmação.
   > [!div class="mx-imgBorder"]
   > ![Mensagem de confirmação em caso de êxito no upload de vários assinantes](media/bulk-add-template-success.png)

## <a name="next-steps"></a>Próximas etapas
- Há apenas um ou dois assinantes para adicionar?  Confira [Adicionar usuários únicos](assign-license.md)
- Saiba como [editar](edit-license.md) assinaturas existentes
- Precisa de ajuda? Contate o [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
