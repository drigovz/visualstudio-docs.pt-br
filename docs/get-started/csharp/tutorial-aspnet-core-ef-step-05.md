---
title: 'Etapa 5: Implantar o aplicativo ASP.NET Core no Azure'
description: Implante seu aplicativo Web ASP.NET Core no Azure com este tutorial em vídeo e instruções passo a passo.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 2d995818ec5b8ac01c9776bbf2290da39d2cc40b
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018097"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Etapa 5: Implantar o aplicativo ASP.NET Core no Azure

Siga estas etapas para implantar seu aplicativo ASP.NET Core e seu banco de dados no Azure.

_Assista a este vídeo e acompanhe-o para implantar primeiro aplicativo Web ASP.NET Core no Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Abrir o projeto

Abra seu aplicativo ASP.NET Core no Visual Studio 2019. O aplicativo já deve estar usando a configuração com o EF Core e uma API Web ativa, conforme configurado na [etapa 4 desta série de tutoriais](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publicar no Serviço de Aplicativo do Azure

Clique com o botão direito do mouse no projeto no gerenciador de soluções e escolha **Publicar**. Mantenha as configurações padrão do **Serviço de Aplicativo** e **Criar Novo** e clique no botão **Publicar**. Se você ainda não tiver uma conta do Azure, clique em **Criar sua conta gratuita do Azure** e conclua o breve processo de registro.

Adicione um SQL Server. Especifique um nome de usuário e senha de administrador.

![Criar SQL Server no Visual Studio 2019](media/vs-2019/vs2019-azure-sql-server.png)

Adicione Application Insights.

Clique no botão **Criar** para continuar.

![Criar novo Serviço de Aplicativo do Azure no Visual Studio 2019](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Explorar o portal do Azure e seu aplicativo hospedado

Depois que o serviço de aplicativo for criado, seu site será iniciado em um navegador. Durante o carregamento, você também pode encontrar o Serviço de Aplicativo no portal do Azure. Ao explorar as opções disponíveis para o serviço de aplicativo, você encontrará uma seção de **Visão Geral** em que é possível iniciar e interromper o aplicativo.

![Opções do Serviço de Aplicativo do Azure](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Dimensionamento

Você pode examinar as opções para escalar verticalmente o aplicativo, bem como horizontalmente. Escalar verticalmente refere-se ao aumento dos recursos fornecidos para cada instância que hospeda seu aplicativo. Escalar horizontalmente refere-se ao aumento do número de instâncias que hospedam seu aplicativo. Você pode configurar o dimensionamento automático para seu aplicativo, o que aumenta automaticamente o número de instâncias usadas para hospedar seu aplicativo em resposta ao carregamento, depois as reduz quando a carga diminuiu.

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

## <a name="see-also"></a>Consulte também

- [Publicar um aplicativo ASP.NET Core no Azure com o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)