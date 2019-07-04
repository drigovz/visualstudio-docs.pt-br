---
title: Definir vários projetos de inicialização no Visual Studio para Mac
description: Este artigo descreve como definir vários projetos para inicialização na execução ou na depuração.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: c692cf8907fcd232b7ba442cea351664bc8dd407
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043602"
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

- [Compilação e criação no Visual Studio para Mac](compiling-and-building.md)
- [Noções sobre configurações de compilação](configurations.md)
