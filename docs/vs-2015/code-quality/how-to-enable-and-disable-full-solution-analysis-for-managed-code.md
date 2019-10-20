---
title: Como habilitar e desabilitar a análise completa da solução para código gerenciado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646288"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Como habilitar e desabilitar a análise completa da solução para código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
> Este tópico aplica-se somente ao Visual Studio 2015 atualização 3 RC e posterior.

 A *análise de solução completa* é um recurso do Visual Studio que permite que você escolha se você vê problemas de análise de C# código somente em arquivos Open Visual ou Visual Basic em sua solução, ou em C# arquivos visuais abertos e fechados ou Visual Basic no seu soluções.

 Embora ser capaz de ver todos os problemas em todos os arquivos seja útil, pode ser uma distração e até mesmo tornar o Visual Studio mais lento se sua solução for muito grande ou tiver muitos arquivos.  Para limitar o número de problemas mostrados e melhorar o desempenho do Visual Studio, você pode desabilitar a análise completa da solução. Você pode reativar esse recurso facilmente se desejar.

#### <a name="to-toggle-full-solution-analysis"></a>Para alternar a análise de solução completa

1. No menu principal do Visual Studio, escolha **ferramentas** &#124; **Opções** para exibir a caixa de diálogo **Opções** .

2. Na caixa de diálogo **Opções** , escolha **Editor** &#124; **C#** de texto ou **básico** &#124; **avançado**.

3. Marque a caixa de seleção **Habilitar análise de solução completa** para habilitar a análise completa da solução ou desmarque a caixa para desabilitá-la. Escolha o botão **OK** quando terminar.

     ![Caixa de seleção Habilitar análise de solução completa.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados da habilitação e desabilitação da análise completa da solução
 Na captura de tela a seguir, você pode ver os resultados quando a análise de solução completa está habilitada. Todos os erros e problemas de análise de código em *todos* os arquivos na solução são exibidos, independentemente de os arquivos estarem abertos ou não.

 ![Análise de solução completa habilitada.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 A captura de tela a seguir mostra os resultados da mesma solução depois de desabilitar a análise de solução completa. Somente os erros e os problemas de análise de código em arquivos de solução aberta aparecem no Lista de Erros.

 ![Análise de solução completa desabilitada.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Desabilitando automaticamente a análise completa da solução
 Se o Visual Studio detectar que 200 MB ou menos memória do sistema está disponível para ele, ele desabilitará automaticamente a análise completa da solução (bem como alguns outros recursos) se ela estiver habilitada. Se isso ocorrer, um alerta será exibido informando sobre isso. Um botão permite reabilitar a análise da solução completa se você quiser fazer isso.

 ![Texto de alerta suspendendo análise de solução completa](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Detalhes adicionais
 Por padrão, a análise de solução completa é habilitada para Visual Basic e C#desabilitada para Visual.

 O Visual Studio atualização 3 RC inclui um mecanismo avançado de diagnóstico do analisador de código v2 que reduz significativamente o uso da memória e diminui o tempo de CPU para ocioso, mesmo que a análise completa da solução esteja habilitada.
