---
title: Configure ferramentas de contêiner visual studio
description: Configure as ferramentas disponíveis no Visual Studio para trabalhar com contêineres Docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188777"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Como configurar ferramentas de contêineres do Visual Studio

Usando as configurações do Visual Studio, você pode controlar alguns aspectos de como o Visual Studio funciona com contêineres Docker, incluindo configurações que afetam o desempenho e o uso de recursos ao trabalhar com contêineres Docker.

## <a name="container-tools-settings"></a>Configurações das ferramentas de contêiner

No menu principal, escolha **Ferramentas > Opções** e expanda **Ferramentas de contêiner > Configurações**. As configurações de ferramentas de contêiner aparecem.

::: moniker range="vs-2017"

![Opções de ferramentas de contêiner do Visual Studio, mostrando: Puxe automaticamente as imagens Docker necessárias na carga do projeto, inicie automaticamente os contêineres em segundo plano, mate automaticamente os contêineres no fechamento da solução e não solicitar a confiança no certificado SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Configurações gerais das ferramentas **de** contêiner:

![Opções de ferramentas de contêiner do Visual Studio, mostrando: Instale o Docker Desktop, se necessário, e o certificado Trust ASP.NET Core SSL.](./media/configure-container-tools/tools-options-1.png)

Configurações **do Projeto Único** de Ferramentas de Contêiner e do **Docker:**

![Opções de ferramentas de contêineres do Visual Studio, mostrando: Mate os contêineres no fechamento do projeto, puxe as imagens docker necessárias na abertura do projeto e execute contêineres no projeto aberto.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

A tabela a seguir pode ajudá-lo a decidir como definir essas opções.

::: moniker range="vs-2017"
| Nome | Configuração padrão | Aplica-se A | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Extração automática das imagens necessárias do Docker no carregamento do projeto | Por | Docker Compose | Para desempenho aprimorado durante o carregamento de projetos, o Visual Studio iniciará uma operação de pull do Docker em segundo plano para que, quando você estiver pronto para executar seu código, a imagem já esteja baixada ou sendo baixada. Se você estiver apenas carregando projetos e procurando código, será possível desativar isso para evitar o download de imagens de contêiner que você não precisa. |
| Início automático dos contêineres em segundo plano | Por | Docker Compose | Novamente, para melhorar o desempenho, o Visual Studio cria um contêiner com montagens de volume prontas para quando você compilar e executar seu contêiner. Se você desejar controlar quando o contêiner é criado, desative essa opção. |
| Encerramento automático dos contêineres na solução | Por | Docker Compose | Desative essa opção se desejar que os contêineres para sua solução continuem a executar após fechar a solução ou fechar o Visual Studio. |
| Não solicitar para confiar no certificado SSL do localhost | Desativado | ASP.NET projetos do Núcleo 2.1 | Se o certificado SSL do localhost não for confiável, o Visual Studio solicitará sempre que você executar seu projeto, a menos que esta caixa de seleção esteja marcada. |
::: moniker-end

::: moniker range=">=vs-2019"

A tabela a seguir descreve configurações **gerais:**

| Nome | Configuração padrão | Aplica-se A | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Instale o Docker Desktop se necessário | Me indistem | Projeto Único, Docker Compor | Escolha se deseja ser solicitado se o Docker Desktop não estiver instalado. |
| Certificado SSL do Trust ASP.NET | Me indistem | ASP.NET Core 2.x | Quando definido **como Prompt Me**, se o certificado SSL localhost não for confiável, o Visual Studio solicitará toda vez que você executar seu projeto. |

A tabela a seguir descreve as configurações **Single Project** e **Docker Compose:**

| Nome | Configuração padrão | Aplica-se A | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Puxe as imagens docker necessárias na abertura do projeto | True | Projeto Único, Docker Compor | Para desempenho aprimorado durante o carregamento de projetos, o Visual Studio iniciará uma operação de pull do Docker em segundo plano para que, quando você estiver pronto para executar seu código, a imagem já esteja baixada ou sendo baixada. Se você estiver apenas carregando projetos e código de navegação, você pode definir como **False** para evitar baixar imagens de contêiner que você não precisa. |
| Executar contêineres em projeto aberto | True | Projeto Único, Docker Compor | Novamente para maior desempenho, o Visual Studio cria um contêiner antes do tempo para que ele esteja pronto para quando você construir e executar seu contêiner. Se você quiser controlar quando seu contêiner for criado, defina **como False**. |
| Pare contêineres no fechamento do projeto | True | Projeto Único e Docker Compõem | Defina como **False** se você quiser que os contêineres para sua solução continuem a ser executados após o fechamento da solução ou o fechamento do Visual Studio. |

::: moniker-end
> [!WARNING]
> Se o certificado SSL localhost não for confiável e você verificar a caixa para suprimir o prompting, as solicitações da Web HTTPS podem falhar no tempo de execução do seu aplicativo ou serviço. Nesse caso, desmarque a caixa de seleção **Não solicitar**, execute seu projeto e indique a confiança no prompt.

## <a name="next-steps"></a>Próximas etapas

Leia mais sobre como trabalhar com contêineres no Visual Studio nesta [visão geral](overview.md).