---
title: Editar assinaturas no portal do de administração | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: Saiba como os administradores podem editar atribuições de assinatura.
ms.openlocfilehash: d145d556467b4eecec787fe409b4faa45945bec0
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232552"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Editar atribuições de assinatura do Visual Studio
Como administrador de assinaturas, você pode fazer alterações nas assinaturas atribuídas às pessoas na organização.  Este artigo descreve os tipos de alterações que você pode fazer e fornece as etapas necessárias.

   > [!NOTE]
   > Se você precisar alterar os detalhes da assinatura para um assinante atribuído através de um Grupo de Diretório Ativo do Azure, você precisará removê-los do grupo e adicioná-los ao Portal de Administração individualmente.  

## <a name="change-subscriber-information"></a>Alterar informações do assinante
Você pode editar as informações do assinante para corrigir erros ou para atualizar as informações.

Para editar um assinante, selecione as reticências (...) que aparecem ao lado do endereço de email do assinante ao passar o mouse sobre ele. Será exibida uma lista suspensa.  Selecione **Editar** para modificar os detalhes do assinante. 
> [!div class="mx-imgBorder"]
> ![Selecione um assinante a ser editado](_img/edit-license/select-subscriber.png)

Você pode atualizar o primeiro nome do assinante, sobrenome, nível de assinatura, endereço de e-mail, país, idioma, downloads e campo de referência. Edite as informações do assinante e clique **em Salvar**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Editar vários assinantes usando a edição em massa
Você pode editar vários assinantes de uma vez usando o processo de edição em massa. Esse recurso é usado principalmente para organizações que estão passando por alterações de endereço de email corporativo ou quando uma organização decide restringir o acesso a downloads.

   > [!IMPORTANT]
   > Os níveis de assinatura (ou seja, Enterprise, Professional, etc.) e GUIDs de assinatura não podem ser alterados usando edição em massa.  Se você precisar atribuir GUIDs de assinatura específicos aos usuários, use o processo para adicionar usuários escolhendo o ID de assinatura. Se você tentar fazer um upload com esses itens alterados no modelo de edição em massa, o upload falhará.

1. Para editar vários assinantes ao mesmo tempo, navegue até a guia Assinantes. Na fita na parte superior, clique em Editar em **massa**.

2. A edição em massa usa um modelo do Excel para fazer edições nas informações dos assinantes. Na caixa De edição em massa, clique **em Exportar este excel** para baixar a lista atual de assinantes, incluindo todas as suas informações.
   > [!div class="mx-imgBorder"]
   > ![Editando uma licença – exportar a lista de edições em massa](_img/edit-license/edit-license-bulk-edit-export.png)

3. Em seguida, salve o arquivo localmente para que ele possa ser encontrado com facilidade e faça as alterações necessárias antes de carregá-lo. Para garantir um upload bem-sucedido, **não edite o nível de assinatura ou o GUID de assinatura** no arquivo de edição em massa, pois isso fará com que o upload falhe.

4. Retorne ao Portal de Administração de Assinaturas do Visual Studio e na caixa de diálogo Edição em Massa, clique em **Procurar**. Selecione o arquivo do Excel que você salvou e clique em **OK**. O andamento do upload será exibido na tela.
   > [!div class="mx-imgBorder"]
   > ![Editando uma licença – upload do arquivo de edições em massa](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Depois de carregar o arquivo, será exibida uma notificação informando que o upload foi bem-sucedido. Neste ponto, suas edições serão refletidas nas informações do assinante.

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
- Precisa atribuir um ID de assinatura específico? Confira Atribuindo um ID de assinatura. 
- Para obter ajuda para encontrar uma assinatura específica, confira [Pesquisar por uma assinatura](search-license.md).
- Precisa criar uma lista de todas as suas assinaturas?  Confira [Exportar assinaturas](exporting-subscriptions.md).


