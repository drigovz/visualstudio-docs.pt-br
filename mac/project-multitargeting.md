---
title: Projetos multidirecionais
description: Este documento fornece uma visão geral de como configurar projetos multiplataforma no Visual Studio para Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451436"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projetos com várias estruturas de destino
No Visual Studio para Mac, você pode configurar um projeto do Xamarin ou do .NET Core para ser executado em qualquer uma das várias versões do .NET Framework e em qualquer uma das várias plataformas do sistema. Por exemplo, você poderia direcionar um projeto para ser executado no .NET Framework 4,6 e no .NET Core 3,1. 

Para obter mais informações sobre estruturas de destino, confira [Estruturas de destino](/dotnet/standard/frameworks).

> [!NOTE] 
> Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, consulte [visão geral de direcionamento da estrutura](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Direcionando várias estruturas

As estruturas de destino são especificadas no arquivo de projeto, que você pode editar clicando com o botão direito do mouse no projeto e escolhendo as **ferramentas > comando Editar arquivo** . Quando uma única estrutura de destino é especificada, use o elemento TargetFramework. O arquivo de projeto de aplicativo de console a seguir demonstra como direcionar o .NET Core 3,0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Use o elemento TargetFrameworks do plural com várias estruturas de destino:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Saiba mais sobre como [direcionar várias estruturas](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Trabalhando com código em um projeto de vários destinos
Ao editar um arquivo C# em um projeto com várias estruturas de destino, você pode especificar qual estrutura de destino você deseja usar para orientar sua experiência de editor (por exemplo, mostrando avisos se você usar uma API sem suporte por essa estrutura). Você pode alterar a estrutura de destino usando o seletor de **estrutura de destino** no canto superior esquerdo da janela do editor.

![Usando o seletor de estrutura de destino para alterar a estrutura de destino, localizada na parte superior da janela do editor](media/project-multitargeting-framework-selector.png)

Às vezes, você precisa chamar diferentes APIs dependendo da plataforma de destino do seu aplicativo. Para fazer isso, você pode escrever código condicional para compilar código para uma plataforma específica:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Ao escrever código, você verá avisos nas sugestões de preenchimento automático do IntelliSense, permitindo que você saiba se as APIs específicas estão ausentes para qualquer uma das estruturas de destino às quais seu aplicativo dá suporte.

![Uma mensagem de aviso mostrada no IntelliSense, uma API não funcionará para uma estrutura de destino especificada. Texto de exemplo: namespace System. buffers, SharedUtils (netstandard 2.0)-não disponível. Você pode usar a barra de navegação para alternar o contexto.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Confira também

- [Visão geral de direcionamento de estrutura (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Estruturas de destino em projetos no estilo SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
