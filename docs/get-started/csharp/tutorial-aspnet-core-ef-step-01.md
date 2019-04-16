---
title: 'Tutorial: Criar um aplicativo Web ASP.NET Core com Entity Framework e Visual Studio 2019'
titleSuffix: ''
description: Como primeira etapa antes de criar um aplicativo Web ASP.NET Core, aprenda como instalar o Visual Studio 2019 com este tutorial em vídeo e instruções passo a passo.
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
ms.openlocfilehash: 711082c70c6174bdf3363ddb12d233ceb3f78f0d
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018110"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Tutorial: Criar seu primeiro aplicativo ASP.NET Core usando Entity Framework com Visual Studio 2019

Neste tutorial, você criará um aplicativo Web ASP.NET Core que usa dados e o implantará no Azure. O tutorial consiste nas seguintes etapas:

- [Etapa 1: Instalar o Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Etapa 2: Criar seu primeiro aplicativo Web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Etapa 3: Trabalhar com dados usando o Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Etapa 4: Expor uma API Web do seu aplicativo ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Etapa 5: Implantar o aplicativo ASP.NET Core no Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Etapa 1: Instalar o Visual Studio 2019

Aprenda como instalar o Visual Studio 2019 com este tutorial em vídeo e instruções passo a passo. Se você já tiver instalado o Visual Studio, vá direto para [Etapa 2: Criar seu primeiro aplicativo Web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md).

_Assista a este vídeo e acompanhe-o para instalar o Visual Studio e criar seu primeiro aplicativo Web ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Baixar o Instalador

Vá para [visualstudio.com](https://visualstudio.com) para localizar o instalador. Localize o link do Visual Studio 2019 e clique nele para iniciar o download. Para obter uma versão gratuita do Visual Studio, escolha Visual Studio Community.

## <a name="start-the-installer"></a>Iniciar o instalador

Após a conclusão do download, clique em **Executar** para iniciar o instalador.

![Instalador do Visual Studio 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Escolha as cargas de trabalho

O Visual Studio pode ser usado para muitos tipos diferentes de desenvolvimento, e as cargas de trabalho facilitam o download de tudo o que é necessário para o tipo de aplicativo que você deseja criar. Escolha as cargas de trabalho **Desenvolvimento de ASP.NET e Web** e **Desenvolvimento de plataforma cruzada .NET Core** por enquanto. Você poderá reiniciar o instalador mais tarde para instalar componentes e cargas de trabalho adicionais.

![Escolher cargas de trabalho no Visual Studio 2019](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Instalar o

Clique em **Instalar** e permitir que o instalador baixe e instale o Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Executar o Visual Studio pela primeira vez

O Visual Studio deve ser iniciado automaticamente quando o instalador for concluído. Você pode ser solicitado a entrar, pois há alguns recursos interessantes associados a ele, mas, por enquanto, você pode optar por fazer isso posteriormente. Em seguida, você pode escolher as configurações de tema e desenvolvimento. Depois de definir essas opções, você estará pronto para iniciar seu primeiro projeto. Clique em **Criar um novo projeto** e, em seguida, escolha **Aplicativo Web ASP.NET Core**.

![Crie novo projeto de aplicativo Web ASP.NET Core no Visual Studio 2019](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Explorar os tipos de projeto do ASP.NET Core

Escolha o nome e o local do projeto e clique em **Criar**. Agora, escolha qual modelo usar em seu aplicativo ASP.NET Core. Você pode escolher entre as seguintes opções:

- Vazio. Um modelo de projeto vazio que permite começar do zero.
- API. O melhor para APIs Web.
- Aplicativo Web. Um aplicativo Web ASP.NET Core padrão criado com Razor Pages.
- Aplicativo Web (Model-View-Controller). Um aplicativo Web ASP.NET Core padrão usando o padrão Model-View-Controller.
- Angular.
- React.js.
- React.js/Redux.
- Biblioteca de classes Razor. Usado para compartilhar ativos Razor entre projetos.

Para a maioria dos modelos de projeto, também é possível habilitar o suporte ao Docker marcando uma caixa. Você também pode adicionar suporte à autenticação clicando no botão Alterar autenticação. Lá, escolha entre:

- Sem Autenticação.
- Contas de Usuários Individuais. Elas são armazenadas em um banco de dados local ou baseado no Azure.
- Contas corporativas ou de estudante. Essa opção usa o Active Directory, Azure AD ou Office 365 para autenticação.
- Autenticação do Windows. Adequada para aplicativos da intranet.

Selecione o modelo de aplicativo Web padrão Sem autenticação e clique em **Ok**.

![Escolher opções de projeto ASP.NET Core no Visual Studio 2019](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Próximas etapas

No próximo vídeo, você aprenderá mais sobre o seu primeiro projeto do ASP.NET Core.

[Tutorial: Criar seu primeiro aplicativo Web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Consulte também

- [Tutorial: Introdução a C# e ASP.NET Core](tutorial-aspnet-core.md) Um tutorial mais detalhado sem instruções em vídeo
