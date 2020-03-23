---
title: Habilite & desativar a análise completa da solução para código gerenciado
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428267"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Como: Habilitar e desativar a análise completa da solução para código gerenciado

*A análise completa da solução* significa que a análise de código examina todos os arquivos C# ou Visual Basic na solução, independentemente de estarem abertos no editor ou não. Por padrão, a análise completa da solução está *habilitada* para o Visual Basic e *desativada* para C#.

Pode ser útil ver todos os problemas em todos os arquivos, mas também pode ser perturbador. Ele retarda o Visual Studio se sua solução é muito grande ou tem muitos arquivos. Para limitar o número de problemas mostrados e melhorar o desempenho do Visual Studio, você pode desativar a análise completa da solução. Você pode facilmente reativar este recurso se necessário.

Na imagem a seguir, a análise completa da solução está ativada. Problemas de análise de código e compilador em todos os arquivos da solução são mostrados, mesmo que não estejam abertos.

![Análise completa da solução habilitada.](../code-quality/media/fsa_enabled.png)

A imagem a seguir mostra os resultados da mesma solução após desativar a análise completa da solução. Apenas erros de compilador e problemas de análise de código em arquivos de solução aberta aparecem na Lista de erros.

![Análise completa da solução desativada.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Alternar análise completa de soluções

1. Para abrir a caixa de diálogo **Opções,** na barra de menus no Visual Studio escolha **Opções de** > **ferramentas**.

1. Na caixa de diálogo **Opções,** escolha **Editor de** > texto**C#** ou **Avançado Básico** > **.**

1. Selecione a **caixa de seleção Ativar análise completa da solução** para permitir a análise completa da solução ou limpar a caixa para desativá-la. Escolha **OK** quando terminar.

   ![Habilite a caixa de seleção completa de análise de solução.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Desativar automaticamente a análise completa da solução

Se o Visual Studio detectar que 200 MB ou menos de memória do sistema está disponível para ele, ele desativará automaticamente a análise completa da solução (e alguns outros recursos) se estiver habilitada. Se isso ocorrer, um alerta aparecerá informando que o Visual Studio desativou alguns recursos. Um botão permite que você rehabilite a análise completa da solução, se quiser.

![Texto de alerta suspendendo análise completa da solução](../code-quality/media/fsa_alert.png)
