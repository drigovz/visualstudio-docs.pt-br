---
title: Editar assinaturas no portal do de administração | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Saiba como os administradores podem editar atribuições de assinatura.
ms.openlocfilehash: e55cee74f861973e3cc29e3f19dc9b31a107f437
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605668"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Editar atribuições de assinatura do Visual Studio
Como administrador de assinaturas, você pode fazer alterações nas assinaturas atribuídas às pessoas na organização.  Este artigo descreve os tipos de alterações que você pode fazer e fornece as etapas necessárias.

## <a name="change-subscriber-information"></a>Alterar informações do assinante
Você pode editar as informações do assinante para corrigir erros ou para atualizar as informações.

Para editar um assinante, selecione as reticências (...) que aparecem ao lado do endereço de email do assinante ao passar o mouse sobre ele. Será exibida uma lista suspensa.  Selecione **Editar** para modificar os detalhes do assinante. Também é possível clicar duas vezes na linha do assinante na grade para abrir a janela de edição.
> [!div class="mx-imgBorder"]
> ![Selecione um assinante a ser editado](_img/edit-license/select-subscriber.png)

Você pode atualizar o nome, o sobrenome, o país, o idioma e os downloads do assinante. Edite as informações do assinante e, em seguida, clique em **Salvar**.

   > [!NOTE]
   > Se você precisar alterar o nível de assinatura de um assinante, será necessário excluir o usuário do portal e adicioná-lo novamente. Os níveis de assinatura não são editáveis.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Editar vários assinantes usando a edição em massa
Você pode editar vários assinantes de uma vez usando o processo de edição em massa. Esse recurso é usado principalmente para organizações que estão passando por alterações de endereço de email corporativo ou quando uma organização decide restringir o acesso a downloads.

   > [!IMPORTANT]
   > Os níveis de assinatura (ou seja, Enterprise, Professional, etc.) e os GUIDs da assinatura não podem ser alterados.  Se você tentar um upload com esses itens alterados, o upload falhará.

1. Para editar vários assinantes de uma vez, navegue até a guia Assinantes. Na faixa de opções na parte superior, clique em **Editar em Massa**.

2. A edição em massa usa um modelo do Excel para fazer edições nas informações dos assinantes. Na caixa Edição em Massa, clique em **Exportar este Excel** para baixar a lista atual de assinantes, incluindo todas as informações deles.
   > [!div class="mx-imgBorder"]
   > ![Editando uma licença – exportar a lista de edições em massa](_img/edit-license/edit-license-bulk-edit-export.png)

3. Em seguida, salve o arquivo localmente para que ele possa ser encontrado com facilidade e faça as alterações necessárias antes de carregá-lo. Para garantir um upload bem-sucedido, **não edite o nível de assinatura nem o GUID da assinatura**, pois isso causaria falha no upload.

4. Retorne ao Portal de Administração de Assinaturas do Visual Studio e na caixa de diálogo Edição em Massa, clique em **Procurar**. Selecione o arquivo do Excel que você salvou e clique em **OK**. O andamento do upload será exibido na tela.
   > [!div class="mx-imgBorder"]
   > ![Editando uma licença – upload do arquivo de edições em massa](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Depois de carregar o arquivo, será exibida uma notificação informando que o upload foi bem-sucedido. Neste ponto, suas edições serão refletidas nas informações do assinante.

## <a name="next-steps"></a>Próximas etapas
- Para obter ajuda para encontrar uma assinatura específica, confira [Pesquisar por uma assinatura](search-license.md).
- Precisa criar uma lista de todas as suas assinaturas?  Confira [Exportar assinaturas](exporting-subscriptions.md).