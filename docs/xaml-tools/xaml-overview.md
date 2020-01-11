---
title: Visão geral do XAML
ms.date: 01/10/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2556387f523769bba93708a9c00d1f7c62429c0f
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886423"
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

O Visual Studio e o Blend para Visual Studio fornecem um Designer XAML que ajuda a criar interfaces do usuário (IU) para aplicativos WPF, UWP e Xamarin.Forms. Você pode arrastar controles das janelas Caixa de ferramentas ou Ativos e definir propriedades na janela Propriedades. Quando você faz isso, o Visual Studio e o Blend para Visual Studio criam o código XAML correspondente. Se você preferir, também poderá editar diretamente o código XAML.

Os artigos neste conjunto de documentação discutem o Designer XAML no Visual Studio e no Blend para Visual Studio.

## <a name="whats-new"></a>O que há de novo

Para obter as informações mais recentes, consulte as novidades [em ferramentas de desenvolvedor XAML na](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/) postagem de blog do visual Studio 2019 e os [novos recursos XAML no vídeo do Visual Studio](https://youtu.be/yI9OyA4ZM2E) sobre o YouTube.

## <a name="see-also"></a>Veja também

- [XAML em aplicativos WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML em aplicativos UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML em aplicativos do Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
