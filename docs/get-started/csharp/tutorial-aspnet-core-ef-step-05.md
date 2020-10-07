---
title: 'Etapa 5: implantando seu aplicativo ASP.NET Core no Azure'
description: Implante seu aplicativo Web ASP.NET Core no Azure com este tutorial em vídeo e instruções passo a passo.
ms.custom: get-started
ms.date: 08/14/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fc0729eccc6f1392561959dcdac0cf13dfc8e04a
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91780948"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Etapa 5: implantar seu aplicativo ASP.NET Core no Azure

Siga estas etapas para implantar seu aplicativo ASP.NET Core e seu banco de dados no Azure.

_Assista a este vídeo e acompanhe-o para implantar primeiro aplicativo Web ASP.NET Core no Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Abrir o projeto

Abra seu aplicativo ASP.NET Core no Visual Studio 2019. O aplicativo já deve estar usando a configuração com o EF Core e uma API Web ativa, conforme configurado na [etapa 4 desta série de tutoriais](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publicar no Serviço de Aplicativo do Azure

1. Clique com o botão direito do mouse no projeto no gerenciador de soluções e escolha **Publicar**. No assistente de **publicação** , escolha **Azure** como o destino.

   ![Captura de tela do serviço de Azure App 1](media/vs-2019/app-service-screen-1.png)

1. Para o destino específico, escolha **serviço de Azure app (Windows)**.

   ![Captura de tela do serviço de Azure App 2](media/vs-2019/app-service-screen-2.png)

1. Escolha **criar um novo serviço de Azure app**. Se você ainda não tiver uma conta do Azure, clique em **Criar sua conta gratuita do Azure** e conclua o breve processo de registro.

   ![Captura de tela do serviço de Azure App 3](media/vs-2019/app-service-screen-3.png)

1. Especifique um nome e um grupo de recursos ou aceite os valores padrão e escolha **criar**. Um grupo de recursos é apenas uma maneira de organizar recursos relacionados no Azure, como serviços que funcionam em conjunto com contas de armazenamento, cofres de chaves e bancos de dados.

   ![Captura de tela do serviço de Azure App 4](media/vs-2019/app-service-screen-4.png)

1. Escolha **Concluir**. Os recursos são criados no Azure, o aplicativo é implantado e a guia **publicar** é preenchida com as informações sobre o que você acabou de criar. A guia **publicar** fornece um botão para publicar com um clique com a mesma configuração, mostra detalhes de configuração ou permite que você adicione serviços como um banco de dados.

Agora, adicione um banco de dados SQL Server do Azure.

1. Na guia **publicar** , em **dependências de serviço**, ao lado de **SQL Server banco de dados**, escolha **Configurar**.

1. Na próxima tela, escolha **banco de dados SQL do Azure**.

   ![Captura de tela do banco de dados SQL do Azure](media/vs-2019/app-service-azure-sql-db.png)

1. Na tela **configurar banco de dados SQL** , escolha **criar um banco de dados SQL**.

   ![Captura de tela de configurar o banco de dados SQL](media/vs-2019/app-service-azure-sql-db-2.png)

1. No **banco de dados SQL do Azure: criar nova** tela, crie um novo servidor de banco de dados.

   ![Captura de tela banco de dados SQL do Azure: criar novo](media/vs-2019/app-service-azure-sql-db-3.png)

1. Na tela **SQL Server: criar nova** , escolha um nome, um local e especifique um nome de usuário e uma senha de administrador.

   ![Criar SQL Server no Visual Studio 2019](media/vs-2019/app-service-azure-sql-db-overlayed.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Explorar o portal do Azure e seu aplicativo hospedado

Depois que o serviço de aplicativo for criado, seu site será iniciado em um navegador. Durante o carregamento, você também pode encontrar o Serviço de Aplicativo no portal do Azure. Ao explorar as opções disponíveis para o serviço de aplicativo, você encontrará uma seção de **Visão Geral** em que é possível iniciar e interromper o aplicativo.

![Opções do Serviço de Aplicativo do Azure](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Escalabilidade

Você pode examinar as opções para dimensionar o aplicativo para cima e para fora. Escalar verticalmente refere-se ao aumento dos recursos fornecidos para cada instância que hospeda seu aplicativo. Escalar horizontalmente refere-se ao aumento do número de instâncias que hospedam seu aplicativo. Você pode configurar o dimensionamento automático para seu aplicativo, o que aumenta automaticamente o número de instâncias usadas para hospedar seu aplicativo em resposta ao carregamento, depois as reduz quando a carga diminuiu.

### <a name="security-and-compliance"></a>Segurança e conformidade

Outro benefício de hospedar o aplicativo usando o Azure é a segurança e conformidade. O Serviço de Aplicativo do Azure fornece conformidade com PCI, SOC e ISO. Podemos autenticar usuários com o Azure Active Directory ou logons sociais, como o Twitter, Facebook, Google ou Microsoft. Podemos criar restrições de IP, gerenciar identidades de serviço, adicionar domínios personalizados e oferecer suporte a SSL para o aplicativo, além de configurar backups com cópias de arquivos mortos restauráveis do conteúdo, da configuração e do banco de dados do aplicativo. Esses recursos são acessados nas opções de menu Autenticação/Autorização, Identidade, Backups e Configurações de SSL.

### <a name="deployment-slots"></a>Slots de implantação

Geralmente, quando você implanta um aplicativo, há um pequeno tempo de inatividade enquanto o aplicativo é reiniciado. Os slots de implantação evitam esse problema, permitindo a implantação em uma instância de preparo separada ou em um conjunto de instâncias, fazendo a preparação antes de colocá-las em produção. A troca é apenas um redirecionamento do tráfego instantâneo e sem problemas. Se houver algum problema na produção após a troca, você poderá reverter a troca para seu último estado de boa produção conhecido.

## <a name="update-connection-string"></a>Atualizar cadeia de conexão

Por padrão, o Azure espera que a conexão de um novo aplicativo ao seu novo banco de dados do SQL Server use uma cadeia de conexão chamada `DefaultConnection`. No momento, o aplicativo criado anteriormente nesta série de tutoriais usa uma cadeia de conexão chamada `AppDbContext`. Precisamos alterar isso em *appsettings.json* e *Startup.cs*, depois reimplantar o aplicativo.

## <a name="test-the-app-running-in-azure"></a>Testar o aplicativo em execução no Azure

Navegue até o caminho */Jogos* para adicionar um novo jogo e vê-lo listado. Em seguida, navegue até o caminho */swagger* para usar os pontos de extremidade da API Web a partir dali, para confirmar que a API do aplicativo está funcionando bem.

Parabéns! Você concluiu esta série de tutoriais em vídeo!

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre como projetar aplicativos ASP.NET Core com esses recursos gratuitos.

[Arquitetura do aplicativo ASP.NET Core](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Confira também

- [Publicar um aplicativo ASP.NET Core no Azure com o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2&preserve-view=true)