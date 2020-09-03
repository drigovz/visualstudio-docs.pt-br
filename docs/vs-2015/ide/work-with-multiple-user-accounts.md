---
title: Trabalhar com várias contas de usuário | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7dc2ba585c500fe045d143a2b8baa2d193466fdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917781"
---
# <a name="work-with-multiple-user-accounts"></a>Trabalhar com várias contas de usuário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você tem várias contas da Microsoft e/ou contas corporativas ou de estudante, é possível adicionar todas elas no Visual Studio para acessar os recursos de qualquer conta sem a necessidade de entrar nas contas separadamente. A partir da data do Visual Studio 2015 RTM, os serviços Azure, Application Insights, Team Foundation Server e Office 365 dão suporte à experiência de entrada simplificada. Serviços adicionais podem ser disponibilizados com o passar do tempo.

 Depois de adicionar várias contas em um computador, esse conjunto de contas se moverá com você ao entrar no Visual Studio em outro computador. É importante observar que, embora os nomes de conta usem perfil móvel, as credenciais não. Portanto, você será solicitado a inserir as credenciais das outras contas na primeira vez que tentar usar os recursos dessas contas no novo computador.

 Este passo a passo mostra como adicionar várias contas no Visual Studio e como ver que os recursos acessíveis dessas contas são refletidos em locais como a caixa de diálogo **Adicionar Serviço Conectado**, o **Gerenciador de Servidores** e o **Team Explorer**.

#### <a name="sign-in-to-visual-studio"></a>Entrar no Visual Studio

1. Entre no Visual Studio 2015 com um conta Microsoft ou uma conta organizacional. Você deve ver seu nome de usuário refletido no canto superior direito da janela, semelhante a este:

     ![Usuário atualmente conectado](../ide/media/vs2015-username.png "VS2015_UserName")

### <a name="access-your-azure-account-in-server-explorer"></a>Acessar sua conta do Azure no Gerenciador de Servidores
 Pressione **Ctrl + Alt + S** abrir o **Gerenciador de Servidores**. Clique no ícone do Azure e, quando ele for expandido, você deverá ver os recursos disponíveis na conta do Azure associada à ID que você usou para fazer logon no Visual Studio 2015. Ele deve ser semelhante a este, exceto que você vê seus próprios recursos, e não o Sr. Guido:

 ![Gerenciador de Servidores mostrando o nó de Ferramentas do Azure expandido](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")

 Na primeira vez que você usar o Visual Studio em qualquer dispositivo específico, a caixa de diálogo mostrará apenas as assinaturas registradas na ID que você usou para entrar no IDE. Você pode acessar os recursos de qualquer uma das outras contas diretamente do **Gerenciador de Servidores** clicando com o botão direito do mouse no nó do Azure e escolhendo **Gerenciar e Filtrar Assinaturas** e, em seguida, adicionar suas contas do controle de seletor de conta. Você pode escolher outra conta, se desejar, clicando na seta para baixo e escolhendo na lista de contas. Depois de escolher a conta, é possível escolher qual assinatura dessa conta você deseja exibir no Gerenciador de Servidores.

 ![Caixa de diálogo Gerenciar assinaturas do Azure](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")

 Na próxima vez que você abrir o Gerenciador de Servidores, os recursos dessa(s) assinatura(s) serão exibidos.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Acessar sua conta do Azure através da caixa de diálogo Adicionar Serviço Conectado

1. Crie um projeto de Aplicativo Universal no C#.

2. Clique com o botão direito do mouse no nó do projeto em Gerenciador de Soluções e escolha **adicionar > serviço conectado**. O assistente Adicionar Serviço Conectado é exibido e mostra a lista de serviços na conta do Azure associada à sua ID de logon do Visual Studio. Observe que você não precisa entrar separadamente no Azure. No entanto, é necessário entrar nas outras contas na primeira vez que você tentar acessar os recursos delas de um determinado computador.

    > [!WARNING]
    > Se esta for a primeira vez que você está criando um aplicativo da Store no Visual Studio 2015 em um computador específico, você será solicitado a habilitar seu dispositivo para o modo de desenvolvimento acessando **configurações &#124;. Atualizações e &#124; de segurança para desenvolvedores** em seu computador. Para obter mais informações, consulte [Habilitar seu dispositivo para desenvolvimento](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).

### <a name="access-azure-active-directory-in-a-web-project"></a><a name="access_azure"></a> Acessar Azure Active Directory em um projeto Web
 O Azure AD habilita o suporte para o logon única do usuário final em aplicativos Web ASP.NET MVC ou autenticação AD nos serviços de API Web. A autenticação de domínio é diferente da autenticação de conta de usuário individual. Os usuários que têm acesso ao seu domínio do Active Directory podem usar suas contas existentes do Azure AD para conectar-se aos aplicativos Web. Os aplicativos do Office 365 também podem usar a autenticação de domínio. Para ver isso em ação, crie um aplicativo Web (**Arquivo > Novo Projeto > C# > Nuvem > Aplicativo Web ASP.NET**). Na caixa de diálogo novo projeto ASP.NET, escolha **alterar autenticação**. O assistente de autenticação aparece e habilita você a escolher o tipo de autenticação a ser usado em seu aplicativo.

 ![Caixa de diálogo Alterar autenticação para ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")

 Para obter mais informações sobre os diferentes tipos de autenticação no ASP.NET, consulte [Creating ASP.NET Web Projects in Visual Studio 2013](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (as informações sobre autenticação ainda são relevantes para o Visual Studio 2015).

### <a name="access-your-visual-studio-team-services-account"></a>Acessar sua conta do Visual Studio Team Services
 No menu principal, escolha **Equipe > Conectar-se ao Team Foundation Server** para mostrar a janela do **Team Explorer**. Clique em **Selecionar Projetos de Equipe**e, em seguida, na caixa de listagem em **Selecionar um Team Foundation Server**, você verá a URL de sua conta do Visual Studio Team Services. Ao selecionar a URL você será conectado sem precisar reinserir suas credenciais.

## <a name="add-a-second-user-account-to-visual-studio"></a>Adicionar uma segunda conta de usuário no Visual Studio
 Clique na seta para baixo ao lado do seu nome de usuário no canto superior direito do Visual Studio. Em seguida, clique no item de menu **configurações de conta** . A caixa de diálogo **Gerenciador de Conta** aparece e exibe a conta com a qual você entrou. Clique no link **Adicionar uma conta** no canto inferior esquerdo da caixa de diálogo para adicionar um novo conta Microsoft ou uma nova conta corporativa ou de estudante.

 ![Seletor de conta do Visual Studio](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")

 Siga as solicitações para ingressar as credenciais da nova conta. A ilustração a seguir mostra o Gerenciador de Conta depois que um usuário adicionou sua conta corporativa Contoso.com.

 ![Gerente de contas](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Rever o Assistente para Adicionar Serviços Conectados e o Gerenciador de Servidores
 Vá novamente até o **Gerenciador de Servidores**, clique com botão direito do mouse no nó do Azure e escolha **Gerenciar e filtrar assinaturas**. Escolha a nova conta, clicando na seta suspensa ao lado da conta atual e, em seguida, escolha quais assinaturas você deseja exibir no Gerenciador de Servidores. Você deve ver todos os serviços associados à assinatura especificada. Mesmo que você não esteja conectado ao IDE do Visual Studio com a segunda conta, você está conectado aos serviços e recursos dessa conta. O mesmo se aplica a **Projeto > Adicionar Serviço Conectado** e **Equipe > Conectar-se ao Team Foundation Server**.
