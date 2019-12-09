---
title: Visão geral do XAML
ms.date: 07/31/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: af6ef98c5bffc4563cfa8fc8e0b29a910aeb85e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601867"
---
# <a name="overview-of-xaml"></a>Visão geral do XAML

XAML (Extensible Application Markup Language) é uma linguagem declarativa baseada em XML. O XAML é usado extensivamente nos seguintes tipos de aplicativos para criar interfaces do usuário:

- [Aplicativos WPF (Windows Presentation Foundation)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Aplicativos da UWP (Plataforma Universal do Windows)](/windows/uwp/xaml-platform/xaml-overview)
- [Aplicativos do Xamarin.Forms](/xamarin/xamarin-forms/xaml/)

O código XAML a seguir define um controle de botão simples.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

O XAML também é usado para definir fluxos de trabalho em [aplicativos do WF (Windows Workflow Foundation)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-designer"></a>XAML Designer

O Visual Studio e o Blend para Visual Studio fornecem um Designer XAML que ajuda a criar interfaces do usuário (IU) para aplicativos WPF, UWP e Xamarin.Forms. Você pode arrastar controles das janelas Caixa de ferramentas ou Ativos e definir propriedades na janela Propriedades. Quando você executa essas ações, o Visual Studio e o Blend para Visual Studio criam o código XAML correspondente. Se você preferir, também poderá editar diretamente o código XAML.

Os artigos neste conjunto de documentação discutem o Designer XAML no Visual Studio e no Blend para Visual Studio.

## <a name="see-also"></a>Consulte também

- [XAML em aplicativos WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML em aplicativos UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML em aplicativos do Xamarin.Forms](/xamarin/xamarin-forms/xaml/)