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
ms.openlocfilehash: 32b3fddd13bd16ac2c846f02f54596ec846374b9
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537485"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Criar exibições personalizadas de dados no depurador do Visual Studio (C#, Visual Basic, C++)

O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depurador fornece várias ferramentas para inspecionar e modificar o estado do programa. A maioria dessas ferramentas funciona somente no modo de interrupção.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Criar exibições personalizadas de dados em janelas de variáveis e DataTips

 Muitas da [janelas do depurador](../debugger/debugger-windows.md), como o **Autos** e **Assista** windows, permitem que você inspecione variáveis. Você pode personalizar como C++ tipos de objetos gerenciados e seus próprios tipos são mostrados nas janelas de variáveis do depurador e, na [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Para obter mais informações, consulte [criar exibições personalizadas de C++ objetos](../debugger/create-custom-views-of-native-objects.md) e [criar exibições personalizadas de objetos](../debugger/create-custom-views-of-dot-managed-objects.md).

## <a name="create-custom-visualizers"></a>Criar visualizadores personalizados

 Os visualizadores permitem exibir o conteúdo de um objeto ou variável de forma significativa. No depurador do Visual Studio, um visualizador refere-se ao windows diferentes que podem ser abertos usando a Lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ícone do visualizador") ícone. Por exemplo, o visualizador HTML mostra como uma cadeia de caracteres HTML seria interpretada e exibida em um navegador. Você pode acessar visualizadores a partir das DataTips, a **Watch** janela, o **Autos** janela e o **locais** janela. O **QuickWatch** caixa de diálogo também fornece um visualizador. Para obter mais informações, confira [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Consulte também

- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Janela Comando](../ide/reference/command-window.md)
- [Segurança do depurador](../debugger/debugger-security.md)