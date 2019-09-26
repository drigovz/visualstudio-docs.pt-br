---
title: Configurar ferramentas de contêiner do Visual Studio
description: Configure as ferramentas disponíveis no Visual Studio para trabalhar com contêineres do Docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: f05eb5d92c0cdaa1242f0d98c3d877eebae27bb1
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253181"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Como configurar as ferramentas de contêiner do Visual Studio

Usando as configurações do Visual Studio, você pode controlar alguns aspectos de como o Visual Studio funciona com contêineres do Docker, incluindo configurações que afetam o desempenho e o uso de recursos ao trabalhar com contêineres do Docker.

## <a name="container-tools-settings"></a>Configurações de ferramentas de contêiner

No menu principal, escolha **Ferramentas > Opções** e expanda **Ferramentas de contêiner > Configurações**. As configurações de ferramentas de contêiner aparecem.

::: moniker range="vs-2017"

![Opções de ferramentas de contêiner do Visual Studio, mostrando: Extração automática das imagens necessárias do Docker no carregamento do projeto, início automático dos contêineres em segundo plano, encerramento automático dos contêineres no fechamento da solução e Não solicitar para confiar no certificado SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Configurações **gerais** das ferramentas de contêiner:

![Opções de ferramentas de contêiner do Visual Studio, mostrando: Instale o Docker desktop, se necessário, e confie ASP.NET Core certificado SSL.](./media/configure-container-tools/tools-options-1.png)

Configurações de **Docker Compose** **projeto único** e ferramentas de contêiner:

![Opções de ferramentas de contêiner do Visual Studio, mostrando: Kill containers no projeto Close, pull de imagens do Docker necessárias no projeto aberto e execute contêineres no projeto aberto.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

A tabela a seguir pode ajudá-lo a decidir como definir essas opções.

::: moniker range="vs-2017"
| Nome | Configuração padrão | Aplica-se a | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Extração automática das imagens necessárias do Docker no carregamento do projeto | On | Docker Compose | Para desempenho aprimorado durante o carregamento de projetos, o Visual Studio iniciará uma operação de pull do Docker em segundo plano para que, quando você estiver pronto para executar seu código, a imagem já esteja baixada ou sendo baixada. Se você estiver apenas carregando projetos e procurando código, será possível desativar isso para evitar o download de imagens de contêiner que você não precisa. |
| Início automático dos contêineres em segundo plano | On | Docker Compose | Novamente, para melhorar o desempenho, o Visual Studio cria um contêiner com montagens de volume prontas para quando você compilar e executar seu contêiner. Se você desejar controlar quando o contêiner é criado, desative essa opção. |
| Encerramento automático dos contêineres na solução | On | Docker Compose | Desative essa opção se desejar que os contêineres para sua solução continuem a executar após fechar a solução ou fechar o Visual Studio. |
| Não solicitar para confiar no certificado SSL do localhost | Off | Projetos ASP.NET Core 2,1 | Se o certificado SSL do localhost não for confiável, o Visual Studio solicitará sempre que você executar seu projeto, a menos que esta caixa de seleção esteja marcada. |
::: moniker-end

::: moniker range=">=vs-2019"

A tabela a seguir descreve as configurações **gerais** :

| Nome | Configuração padrão | Aplica-se a | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Instalar o Docker desktop, se necessário | Avisar-me | Único projeto, Docker Compose | Escolha se deseja ser solicitado se o Docker desktop não estiver instalado. |
| Confiar ASP.NET Core certificado SSL | Avisar-me | Projetos ASP.NET Core 2. x | Quando definido como **avisar**, se o certificado SSL do localhost não for confiável, o Visual Studio será notificado sempre que você executar o projeto. |

A tabela a seguir descreve o **projeto único** e as configurações de **Docker Compose** :

| Nome | Configuração padrão | Aplica-se a | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Efetuar pull de imagens do Docker necessárias no projeto aberto | verdadeiro | Único projeto, Docker Compose | Para desempenho aprimorado durante o carregamento de projetos, o Visual Studio iniciará uma operação de pull do Docker em segundo plano para que, quando você estiver pronto para executar seu código, a imagem já esteja baixada ou sendo baixada. Se você estiver apenas carregando projetos e navegando em código, poderá definir como **false** para evitar o download de imagens de contêiner desnecessárias. |
| Executar contêineres no projeto aberto | verdadeiro | Único projeto, Docker Compose | Novamente para melhorar o desempenho, o Visual Studio cria um contêiner antecipadamente para que ele esteja pronto para quando você compilar e executar seu contêiner. Se você quiser controlar quando seu contêiner é criado, defina como **false**. |
| Parar contêineres no fechamento do projeto | verdadeiro | Único projeto e Docker Compose | Defina como **false** se desejar que os contêineres da solução continuem a ser executados depois de fechar a solução ou fechar o Visual Studio. |

::: moniker-end
> [!WARNING]
> Se o certificado SSL do localhost não for confiável e você marcar a caixa para suprimir a solicitação, as solicitações da Web HTTPS poderão falhar em tempo de execução em seu aplicativo ou serviço. Nesse caso, desmarque a caixa de seleção **Não solicitar**, execute seu projeto e indique a confiança no prompt.

## <a name="next-steps"></a>Próximas etapas

Leia mais sobre como trabalhar com contêineres no Visual Studio nesta [visão geral](visual-studio-tools-for-docker.md).