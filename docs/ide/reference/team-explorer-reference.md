---
title: Referência do Team Explorer
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: 6a7c1e9d0f5e8b8ef48a033d58038818d2d620e5
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222968"
---
# <a name="team-explorer-reference"></a>Referência do Team Explorer

Este artigo fornece links para artigos do Azure DevOps sobre as várias funções no **Team Explorer**.

Use a janela de ferramentas **Team Explorer** para coordenar seus esforços de codificação com outros membros da equipe para desenvolver um projeto e gerenciar o trabalho atribuído a você, sua equipe ou seus projetos. O **Team Explorer** conecta o Visual Studio a repositórios Git e GitHub, repositórios do TFVC (Controle de Versão do Team Foundation) e projetos hospedados no [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) ou em um [Azure DevOps Server](/tfs/index) local (anteriormente conhecido como TFS). Você pode gerenciar o código-fonte, itens de trabalho e builds.

## <a name="home-page"></a>Home page

Depois que você se [conectar a um projeto](../connect-team-project.md) no **Team Explorer**, os seguintes links ficarão disponíveis na seção **Projeto**:

- [Clonar repositório](/azure/devops/repos/git/clone)
- [Portal da Web](/azure/devops/project/navigation/index)
- [Painel de tarefas](/azure/devops/boards/sprints/task-board)

A página **Página Inicial** tem funções diferentes dependendo se você está conectado a um repositório [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) ou [TFVC (Controle de Versão do Team Foundation)](/azure/devops/repos/tfvc/overview).

> [!TIP]
> Para obter uma comparação dos dois sistemas de controle de versão, confira [Escolher o controle de versão certo para seu projeto (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| Página **Página Inicial** com o Git | Página **Página Inicial** com o TFVC |
| - | - |
| ![Home page do Team Explorer com o Git no Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Home page do Team Explorer com o TFVC no Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Página Alterações (Git)

Confira [Salvar o trabalho com confirmações](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Página Branches (Git)

Confira [Criar trabalho em branches](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Página Solicitações de Pull (Git)

Confira [Examinar o código com solicitações de pull](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Página Sincronização (Git)

Confira [Atualizar o código com fetch e pull](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Página Marcas (Git)

Confira [Trabalhar com marcas do Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Página Meu trabalho (TFVC)

Confira [Suspender/retomar o trabalho](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) e [Revisão de código](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Página Alterações Pendentes (TFVC)

Confira [Gerenciar alterações pendentes](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [Localizar check-ins particulares](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) e [Resolver conflitos](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Página Source Control Explorer (TFVC)

Confira [Exibir/adicionar arquivos e pastas](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Página Itens de Trabalho

A página **Itens de Trabalho** permite que você veja as consultas de [item de trabalho](/azure/devops/boards/work-items/about-work-items). Consulte:

- [Adicionar itens de trabalho](/azure/devops/boards/backlogs/add-work-items)
- [Usar o editor de consultas para listar e gerenciar consultas](/azure/devops/boards/queries/using-queries)
- [Organizar pastas de consulta e definir permissões de consulta](/azure/devops/boards/queries/set-query-permissions)
- [Abrir a consulta no Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Abrir a consulta no Projeto](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Lista de resultados da consulta de email usando o Outlook](/azure/devops/boards/queries/share-plans)
- [Criar relatórios com base na consulta no Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (somente TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> Há uma nova [experiência de Itens de Trabalho](/azure/devops/boards/work-items/set-work-item-experience-vs) no Visual Studio 2019. Para obter informações sobre como exibir itens de trabalho no Visual Studio 2019, confira [Exibir e adicionar itens de trabalho](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Página Builds

A página **Builds** permite que você veja as definições de build do projeto.

Consulte:

- [Criar pipelines de build](/azure/devops/pipelines/tasks/index)
- [Exibir e gerenciar builds](/azure/devops/pipelines/overview)
- [Gerenciar a fila de builds](/azure/devops/pipelines/agents/pools-queues)
- [Instalar as Ferramentas de Entrega Contínua para Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Configurar e executar a CD (entrega contínua) para o aplicativo](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Página Configurações

A página **Configurações** permite configurar funcionalidades administrativas para um projeto ou uma coleção de projetos. Confira os seguintes artigos:

| Projeto | Coleção de projetos | Outros |
| - | - | - |
| [Segurança, associação a um grupo](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Segurança, controle do código-fonte (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Áreas de itens de trabalho](/azure/devops/organizations/settings/set-area-paths)<br/>[Iterações de item de trabalho](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Configurações do portal](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Alertas do projeto](/azure/devops/notifications/howto-manage-team-notifications) | [Segurança, associação a um grupo](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Controle do código-fonte (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Gerenciador de Modelos de Processo](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Configurações globais do Git](/azure/devops/repos/git/git-config)<br/>[Configurações do repositório Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Consulte também

- [Conectar-se a projetos no Team Explorer](../../ide/connect-team-project.md)