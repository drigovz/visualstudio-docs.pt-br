---
title: Definir vários projetos de inicialização
description: Este artigo descreve como definir vários projetos para inicialização na execução ou na depuração.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: df1e088a5e2d0f65d8b72dad0895f1edb1740f1f
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493563"
---
# <a name="set-multiple-startup-projects"></a>Definir vários projetos de inicialização

O Visual Studio para Mac permite especificar que mais de um projeto deve ser iniciado quando você depura ou executa sua solução.

## <a name="to-set-multiple-startup-projects"></a>Para definir vários projetos de inicialização

1. Na janela da solução, selecione a solução (o nó superior).

2. Clique com o botão direito do mouse no nó da solução e selecione **Definir Projetos de Inicialização** :

   ![Selecionar Definir Projetos de Inicialização](media/startup-proj-ctx-menu.png)

3. A caixa de diálogo **Criar Configuração de Execução da Solução** é aberta. Essa caixa de diálogo permite criar uma nova Configuração de Execução da Solução nomeada para a solução. Você pode usar qualquer nome que quiser. O nome padrão é `Multiple Projects`.

   ![Caixa de diálogo Criar Configuração de Execução da Solução](media/create-sln-run-config.png)

4. Selecione **Criar Configuração de Execução**. A caixa de diálogo **Opções da Solução** é aberta com a nova Configuração de Execução da Solução selecionada:

   ![Caixa de diálogo Opções da Solução](media/sln-options-run-config-multi-projects.png)

5. Selecione os projetos que deseja iniciar ao depurar ou executar seu aplicativo no Visual Studio para Mac:

   ![Caixa de diálogo Opções da Solução com projetos selecionados](media/sln-options-run-config-multi-projects-configured.png)

6. Selecione **OK**. A nova Configuração de Execução da Solução é definida como a configuração de execução ativa:

   ![Solução com vários projetos configurados para começar a depuração ou execução](media/startup-project-configured.png)

   Agora, os dois projetos são configurados para iniciar, que é representado por ambos os projetos que aparecem em **negrito** na janela da solução. Na barra de ferramentas, a nova configuração de execução é definida como a Configuração de Execução da Solução atual.

## <a name="next-steps"></a>Próximas etapas

- [Compilando e compilando em Visual Studio para Mac](compiling-and-building.md)
- [Noções sobre configurações de build](configurations.md)
