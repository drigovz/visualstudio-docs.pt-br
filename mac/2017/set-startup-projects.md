---
title: Definir vários projetos de inicialização no Visual Studio para Mac
description: Este artigo descreve como definir vários projetos para inicialização na execução ou na depuração.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: a4a4f2f4fd4ce6cd88d11979a21e4e9184adfca8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988451"
---
# <a name="how-to-set-multiple-startup-projects"></a>Como: Definir vários projetos de inicialização

O Visual Studio para Mac permite que você especifique como mais de um projeto é iniciado ao depurar ou executar sua solução.

## <a name="to-set-multiple-startup-projects"></a>Para definir vários projetos de inicialização

1. No **Painel de Soluções**, selecione a solução (o nó superior).

2. Escolha o menu de contexto (de atalho) do nó da solução e, em seguida, escolha **Definir Projetos de Inicialização…**.

   ![Menu de contexto Definir projetos de inicialização](media/startup-proj-ctx-menu.png)

3. A caixa de diálogo **Criar Configuração de Execução da Solução** será exibida. Essa caixa de diálogo criará uma Configuração de Execução da Solução nomeada para a solução. Você pode fornecer a ela qualquer nome que desejar; o nome padrão é `Multiple Projects`.

   ![Caixa de diálogo Criar Configuração de Execução da Solução](media/create-sln-run-config.png)

4. Clique em **Criar Configuração de Execução**. A caixa de diálogo **Opções da Solução** será aberta com a nova Configuração de Execução da Solução selecionada.

   ![Caixa de diálogo Opções da Solução](media/sln-options-run-config-multi-projects.png)

5. Selecione os projetos que deseja iniciar ao depurar ou executar seu aplicativo no Visual Studio para Mac.

   ![Caixa de diálogo Opções da Solução com a configuração de execução definida](media/sln-options-run-config-multi-projects-configured.png)

6. Clique em **OK**. A caixa de diálogo será ignorada e a nova Configuração de Execução da Solução será definida como a configuração de execução ativa.

   ![Solução com vários projetos configurados para serem iniciados na depuração ou na execução](media/startup-project-configured.png) Você pode ver que dois projetos estão configurados para serem iniciados, pois ambos os projetos estão em **negrito** no **Painel de Soluções**. Na barra de ferramentas, a nova configuração de execução é definida como a Configuração de Execução da Solução atual.

## <a name="next-steps"></a>Próximas etapas

- [Compilação e criação no Visual Studio para Mac](compiling-and-building.md)
- [Noções sobre configurações de compilação](configurations.md)