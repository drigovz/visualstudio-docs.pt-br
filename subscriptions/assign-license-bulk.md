---
title: Atribuir licenças a grupos de usuários para assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: Saiba como os administradores podem atribuir licenças a vários assinantes usando o recurso Bulk add ou os grupos de diretórioativo ativo do Microsoft Azure
ms.openlocfilehash: eb641d86733ef794f1d53ae6eee45e0bdf4fde18
ms.sourcegitcommit: deab74e8f41b30b28c041b048d67b3fff2cceab9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80994447"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Atribuir assinaturas a vários usuários
O portal de administração de assinaturas permite que você adicione usuários individualmente ou em grupos grandes.  Para adicionar usuários únicos, confira [Adicionar usuários únicos](assign-license.md).

Para adicionar grandes grupos de usuários, você pode usar o recurso de adicionar em massa, ou se sua organização estiver usando o Microsoft Azure Active Directory (Azure AD), você pode usar grupos Azure AD. Este artigo explicará o processo para ambas as opções. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Use bulk add para atribuir assinaturas
1. Inscreva-se no Portal de https://manage.visualstudio.comAdministração de Assinaturas do Visual Studio em .

2. Para adicionar vários assinantes ao mesmo tempo, navegue até a guia **Gerenciar assinantes.** Escolha a guia **Adicionar** e, em seguida, escolha Adicionar em **massa** no down-down.  

2. O bulk add usa um modelo do Microsoft Excel para carregar informações de assinantes. Na caixa de diálogo Carregar Vários Assinantes, clique em **Baixar** para baixar o modelo.
   > [!div class="mx-imgBorder"]
   > ![Baixar o modelo do Excel para carregar vários assinantes](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Sempre baixe a versão mais recente deste modelo. Se você usar uma versão mais antiga, o upload em massa poderá falhar.

3. Na planilha do Excel, preencha os campos com as informações dos indivíduos aos quais deseja atribuir assinaturas. (*A referência* é um campo opcional.) Salve o arquivo localmente depois que terminar.

   Para que não haja problemas com o upload, observe as seguintes melhores práticas:

    - Verifique se nenhum dos campos do formulário contém vírgulas.
    - Remova os espaços antes e depois de campos de formulário.
    - Verifique se os nomes do usuário não contêm espaços extras entre nomes ou sobrenomes de duas partes (por exemplo, se uma pessoa tiver um nome de duas partes, como "Maria Eduarda", ele deverá ser digitado como "MariaEduarda", porque o sistema não cortará o espaço extra).
    - Certifique-se de que todos os campos necessários estão concluídos. 
    - Verifique a coluna **de mensagem de erro.**  Se algum erro estiver listado, resolva-os antes de tentar carregar o arquivo. 

4. Retorne ao portal de Administração de Assinaturas do Visual Studio. Na caixa de diálogo **Carregar Vários Assinantes**, clique em **Procurar**.
   > [!div class="mx-imgBorder"]
   > ![Navegar para o modelo salvo para carregar vários assinantes](media/bulk-add-browse-saved-template.png)

5. Navegue para o arquivo do Excel que você salvou e, em seguida, clique em **OK**.
   > [!div class="mx-imgBorder"]
   > ![Carregar o modelo do Excel para carregar vários assinantes](media/bulk-upload-subscribers.png)

    Uma caixa de diálogo de progresso do upload será exibida.

    Se o modelo contiver erros, o upload falhará e os erros serão mostrados para que você possa corrigir o modelo e tentar o upload em massa novamente.
   > [!div class="mx-imgBorder"]
   > ![Mensagem de erro em caso de falha no upload de vários assinantes](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Se você encontrar uma falha, siga estas etapas:
   1. Abra o arquivo Excel que você criou, corrija os problemas e salve o arquivo.
   0. Retorne ao Portal de Administração e escolha **Adicionar**.
   0. Selecione **adicionar em massa**.
   0. Como você já tem o arquivo Excel salvo, você não precisa baixar o modelo.  Clique **em Procurar,** localize o arquivo que você acabou de salvar e clique em **Abrir**.
   0. Clique em **OK**.


    Quando o upload for bem-sucedido, você verá a lista de assinantes e uma mensagem de confirmação.
   > [!div class="mx-imgBorder"]
   > ![Mensagem de confirmação em caso de êxito no upload de vários assinantes](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Use grupos de diretórios ativos do Azure para atribuir assinaturas 
O uso deste recurso facilita a permanência em suas atribuições de assinatura. Você pode adicionar Grupos de Segurança do Diretório Ativo do Azure no Portal de Administração de Assinaturas, que garantirá que todos os indivíduos do grupo sejam designados para uma assinatura. E para facilitar, quando os indivíduos deixam sua organização e são removidos do Azure Active Directory, seu acesso a assinaturas também é removido. 


> [!IMPORTANT]
>
> As seguintes limitações se aplicam ao uso de grupos AD do Azure para adicionar assinantes:
> - Os grupos devem conter pelo menos um membro.  Grupos vazios não são suportados.
> - Grupos devem ter menos de 1.000 usuários 
> - Todos os usuários devem estar no nível superior do grupo.  Grupos aninhados não são suportados
> - Apenas acordos confiáveis são suportados
> - Todos os membros do grupo devem ter um endereço de e-mail associado à sua conta Azure AD
> - Endereços de e-mail separados para notificações não são suportados para assinaturas adicionadas usando grupos AD do Azure.  

1. Faça login no Portal de Administração [https://manage.visualstudio.com](https://manage.visualstudio.com)de Assinaturas do Visual Studio em .

2. Para adicionar vários assinantes ao mesmo tempo, navegue até a guia **Gerenciar assinantes.**

3. Escolha a guia **Adicionar** e selecione **o grupo Diretório ativo do Azure** na queda.  

   > [!div class="mx-imgBorder"]
   > ![Escolha adicionar em massa usando o Azure AD](_img/assign-license-bulk/bulk-add-aad.png)

4. Comece a inserir o nome do grupo Azure AD que você gostaria de adicionar no campo de formulário. Isso irá pesquisar os grupos AD disponíveis do Azure dentro da sua organização. 

5. Quando você selecionar o grupo, o campo será preenchido automaticamente com o nome do grupo. Você terá a opção de visualizar os usuários desse grupo antes de adicioná-los. Em seguida, você pode escolher o nível de assinatura, os direitos de download e as preferências de comunicação para o grupo. Você pode adicionar detalhes no campo de referência, se desejar. 

   > [!div class="mx-imgBorder"]
   > ![Escolha adicionar em massa usando o Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Clique **em Adicionar** e, em seguida, **Confirmar**. 

7. Para ver o grupo adicionado, role até a parte inferior da sua lista de usuários.  

8. Selecione **Exibir assinantes** para exibir os membros do grupo. Você pode ver detalhes sobre os assinantes do grupo, mas não pode fazer nenhuma edições para os assinantes ou as assinaturas que eles são atribuídos.    

> [!NOTE]
> Se você já tiver atribuído assinaturas individualmente aos usuários que são adicionados posteriormente como parte de um grupo AD do Azure, eles serão adicionados como parte do grupo e não serão mais listados individualmente. No entanto, se a assinatura individual for para um nível de assinatura diferente, eles terão duas assinaturas.  Exemplo: Se um usuário tiver uma assinatura individual do Visual Studio Professional e for membro de um grupo ao qual você atribui assinaturas do Visual Studio Enterprise, ele terá ambos.  


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>Perguntas frequentes
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>P: Posso escolher vários níveis de assinatura a serem atribuídos dentro de um grupo AD do Azure? 
A: Não - todos no grupo recebem a mesma assinatura. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>P: Posso editar detalhes de assinantes de indivíduos adicionados em um grupo Azure AD?  
A: Não - Para modificar as informações para um assinante individual, você precisará removê-las do grupo de segurança Azure AD e atribuir-lhes uma assinatura individualmente.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>P: Eu adicionei alguém ao meu grupo de segurança Azure AD, mas não os vejo adicionados no Portal de Administração de Assinaturas, e eles não têm uma assinatura. Por que não?  
R: Dependendo de como sua organização configurou o Azure AD, você pode ver atrasos de até 24 horas antes de o usuário ser adicionado. Se for mais de 24 horas, [contate o suporte.](https://visualstudio.microsoft.com/support/support-overview-vs)  

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
- Há apenas um ou dois assinantes para adicionar?  Confira [Adicionar usuários únicos](assign-license.md)
- Precisa de ajuda? Contate o [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
