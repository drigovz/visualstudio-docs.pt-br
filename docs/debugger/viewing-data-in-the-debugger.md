---
title: Criar exibições personalizadas de dados no depurador | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63dc11736e92013719fcda2bae0ba9599a8835aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72568997"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Criar exibições personalizadas de dados no depurador do Visual Studio (C#, Visual Basic, C++)

O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depurador fornece muitas ferramentas para inspecionar e modificar o estado do seu programa. A maioria dessas ferramentas funciona somente no modo de interrupção.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Criar exibições personalizadas de dados em janelas variáveis e DataTips

 Muitas das [janelas do depurador](../debugger/debugger-windows.md), como as janelas **automáticas** e de **inspeção** , permitem inspecionar variáveis. Você pode personalizar a forma como os tipos de C++, os objetos gerenciados e seus próprios tipos são mostrados na variável de depurador Windows e em [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Para obter mais informações, consulte [criar exibições personalizadas de objetos C++](../debugger/create-custom-views-of-native-objects.md) e [criar exibições personalizadas de objetos gerenciados](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Criar visualizadores personalizados

 Os visualizadores permitem exibir o conteúdo de um objeto ou variável de uma maneira significativa. No depurador do Visual Studio, um visualizador refere-se às diferentes janelas que você pode abrir usando o ícone de ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ícone do Visualizador") de lupa. Por exemplo, o Visualizador de HTML mostra como uma cadeia de caracteres HTML seria interpretada e exibida em um navegador. Você pode acessar os visualizadores de DataTips, a janela de **inspeção** , a janela **autos** e a janela **locais** . A caixa de diálogo **QuickWatch** também fornece um visualizador. Para obter mais informações, consulte [criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Confira também

- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Janela Comando](../ide/reference/command-window.md)
- [Segurança do depurador](../debugger/debugger-security.md)
