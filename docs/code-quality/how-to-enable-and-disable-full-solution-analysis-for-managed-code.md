---
title: Habilitar & desabilitar a análise completa da solução para o código gerenciado
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3f7837b1e5ea5b84e1ee1197bf6f8c40d0863c3e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649454"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Como habilitar e desabilitar a análise completa da solução para código gerenciado

*Análise de solução completa* significa que a análise de código examina C# todos os arquivos de Visual Basic na solução, independentemente de eles estarem abertos ou não no editor. Por padrão, a análise de solução completa é *habilitada* para Visual Basic C#e *desabilitada* para.

Pode ser útil ver todos os problemas em todos os arquivos, mas também pode ser confuso. Isso reduzirá o Visual Studio se sua solução for muito grande ou tiver muitos arquivos. Para limitar o número de problemas mostrados e melhorar o desempenho do Visual Studio, você pode desabilitar a análise completa da solução. Você pode reabilitar esse recurso facilmente, se necessário.

Na imagem a seguir, a análise de solução completa está habilitada. Os problemas de análise de compilador e de código em todos os arquivos na solução são mostrados, mesmo que não estejam abertos.

![Análise de solução completa habilitada.](../code-quality/media/fsa_enabled.png)

A imagem a seguir mostra os resultados da mesma solução depois de desabilitar a análise de solução completa. Somente erros de compilador e problemas de análise de código em arquivos de solução aberta aparecem no Lista de Erros.

![Análise de solução completa desabilitada.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Alternar análise de solução completa

1. Para abrir a caixa de diálogo **Opções** , na barra de menus do Visual Studio, escolha **ferramentas** > **Opções**.

1. Na caixa de diálogo **Opções** , escolha **o Editor** de**C#** texto  >  ou **Basic**  > **avançado**.

1. Marque a caixa de seleção **Habilitar análise de solução completa** para habilitar a análise completa da solução ou desmarque a caixa para desabilitá-la. Escolha **OK** quando terminar.

   ![Caixa de seleção Habilitar análise de solução completa.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Desabilitar automaticamente a análise completa da solução

Se o Visual Studio detectar que 200 MB ou menos de memória do sistema está disponível para ele, ele desabilitará automaticamente a análise completa da solução (e alguns outros recursos) se ela estiver habilitada. Se isso ocorrer, um alerta será exibido informando que o Visual Studio desabilitou alguns recursos. Um botão permite reabilitar A análise da solução completa, se desejar.

![Texto de alerta suspendendo análise de solução completa](../code-quality/media/fsa_alert.png)
