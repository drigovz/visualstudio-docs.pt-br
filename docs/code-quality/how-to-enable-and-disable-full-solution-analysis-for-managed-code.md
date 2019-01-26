---
title: 'Como: Habilitar e desabilitar análise de solução completa para código gerenciado'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- dotnet
ms.openlocfilehash: ffda04828789a591c0e6dca35ef391fe6b8556d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035465"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Como: Habilitar e desabilitar análise de solução completa para código gerenciado

*Análise de solução completa* é um recurso do Visual Studio que permite que você veja problemas de análise de código somente em arquivos abertos de Visual c# ou Visual Basic em sua solução, ou também em código, arquivos que estão fechadas. Por padrão, a análise de solução completa é *habilitados* para o Visual Basic, e *desabilitada* do Visual c#.

Pode ser útil ver todos os problemas em todos os arquivos, mas também pode ser distração. Ele desacelera Visual Studio se sua solução for muito grande ou tiver vários arquivos. Para limitar o número de problemas mostrados e melhorar o desempenho do Visual Studio, você pode desabilitar análise completa da solução. Você pode facilmente habilitar este recurso novamente se necessário.

## <a name="to-toggle-full-solution-analysis"></a>Para ativar/desativar a análise de solução completa

1. Para abrir o **opções** caixa de diálogo, na barra de menus no Visual Studio escolher **ferramentas** > **opções**.

1. No **opções** diálogo caixa, escolha **Editor de texto** > **c#** ou **básica**  >   **Advanced**.

1. Selecione o **habilitar a análise de solução completa** caixa de seleção para habilitar a análise de solução completa, ou desmarque a caixa para desativá-lo. Escolher **Okey** quando você terminar.

    ![Habilite a caixa de seleção de análise de solução completa.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados de habilitar e desabilitar análise de solução completa

Na seguinte captura de tela, você pode ver os resultados quando a análise de solução completa está habilitada. Todos os erros e problemas de análise de código em *todos os* dos arquivos na solução exibido, independentemente se os arquivos estão abertos ou não.

![Análise completa da solução habilitada.](../code-quality/media/fsa_enabled.png)

Captura de tela a seguir mostra os resultados da mesma solução depois de desabilitar análise completa da solução. Somente os erros e problemas de análise de código em arquivos de solução aberta que aparecem na **Error List**.

![Análise de solução completa desabilitado.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Desabilitar automaticamente a análise de solução completa

Se o Visual Studio detectar que 200 MB ou menos da memória do sistema está disponível para ele, ele automaticamente desabilita a análise completa da solução (e alguns outros recursos) se ele estiver habilitado. Se isso ocorrer, um alerta será exibida informando que o Visual Studio desabilitou a alguns recursos. Um botão permite que você reabilitar se você quiser que a análise de solução completa.

![Suspendendo a análise de solução completa de texto de alerta](../code-quality/media/fsa_alert.png)