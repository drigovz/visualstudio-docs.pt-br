---
title: Definir vários projetos de inicialização
description: Este artigo descreve como definir vários projetos para inicialização na execução ou na depuração.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 55519960a6b84968ced43183833167a365e91b35
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68872318"
---
# <a name="set-multiple-startup-projects"></a>Definir vários projetos de inicialização

O Visual Studio para Mac permite especificar que mais de um projeto deve ser iniciado quando você depura ou executa sua solução.

## <a name="to-set-multiple-startup-projects"></a>Para definir vários projetos de inicialização

1. No Painel de Soluções, selecione a solução (o nó superior).

2. Clique com o botão direito do mouse no nó da solução e selecione **Definir Projetos de Inicialização**:

   ![Selecionar Definir Projetos de Inicialização](media/startup-proj-ctx-menu.png)

3. A caixa de diálogo **Criar Configuração de Execução da Solução** é aberta. Essa caixa de diálogo permite criar uma nova Configuração de Execução da Solução nomeada para a solução. Você pode usar qualquer nome que quiser. O nome padrão é `Multiple Projects`.

   ![Caixa de diálogo Criar Configuração de Execução da Solução](media/create-sln-run-config.png)

4. Selecione **Criar Configuração de Execução**. A caixa de diálogo **Opções da Solução** é aberta com a nova Configuração de Execução da Solução selecionada:

   ![Caixa de diálogo Opções da Solução](media/sln-options-run-config-multi-projects.png)

5. Selecione os projetos que deseja iniciar ao depurar ou executar seu aplicativo no Visual Studio para Mac:

   ![Caixa de diálogo Opções da Solução com projetos selecionados](media/sln-options-run-config-multi-projects-configured.png)

6. Selecione **OK**. A nova Configuração de Execução da Solução é definida como a configuração de execução ativa:

   ![Solução com vários projetos configurados para começar a depuração ou execução](media/startup-project-configured.png)

   Você pode ver que os dois projetos estão configurados para iniciar, pois ambos os projetos estão **em negrito** no Painel de Soluções. Na barra de ferramentas, a nova configuração de execução é definida como a Configuração de Execução da Solução atual.

## <a name="next-steps"></a>Próximas etapas

- [Compilação e construção em Visual Studio para Mac](compiling-and-building.md)
- [Entendendo as configurações de construção](configurations.md)
