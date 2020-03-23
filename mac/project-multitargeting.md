---
title: Projetos multisegmentantes
description: Este documento fornece uma visão geral de como configurar projetos multidirecionados no Visual Studio para Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451436"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projetos com múltiplas estruturas de destino
No Visual Studio for Mac, você pode configurar um projeto Xamarin ou .NET Core para ser executado em qualquer uma das várias versões do .NET Framework, e em qualquer uma das várias plataformas do sistema. Por exemplo, você pode direcionar um projeto para ser executado em ambos .NET Framework 4.6 e .NET Core 3.1. 

Para obter mais informações sobre estruturas de destino, confira [Estruturas de destino](/dotnet/standard/frameworks).

> [!NOTE] 
> Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, consulte [Visão geral do framework targeting](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Visando múltiplas estruturas

As estruturas de destino são especificadas no arquivo do projeto, que você pode editar clicando com o botão direito do mouse no seu projeto e escolhendo o comando **Ferramentas > Editar arquivo.** Quando uma única estrutura de destino é especificada, use o elemento TargetFramework. O arquivo de projeto do aplicativo de console a seguir demonstra como segmentar o .NET Core 3.0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Use o elemento Plural TargetFrameworks com várias frameworks de destino:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Saiba mais sobre como [segmentar várias estruturas](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Trabalhando com código em um projeto multi-target
Quando você está editando um arquivo C# em um projeto com várias frameworks de destino, você pode especificar qual estrutura de destino você deseja usar para orientar a experiência do editor (por exemplo, mostrando avisos se você usar uma API não suportada por essa estrutura). Você pode alterar a estrutura de destino usando o seletor **Target Framework** no canto superior esquerdo da janela do editor.

![Usando o seletor de quadro de destino para alterar a estrutura de destino, localizada na parte superior da janela do editor](media/project-multitargeting-framework-selector.png)

Às vezes, você precisa chamar diferentes APIs dependendo da plataforma que seu aplicativo está mirando. Para fazer isso, você pode escrever código condicional para compilar código para uma plataforma específica:

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

Ao escrever código, você verá avisos em sugestões de conclusão automática do IntelliSense, informando se apIs específicas estão faltando para qualquer uma das estruturas de destino que seu aplicativo suporta.

![Uma mensagem de aviso mostrada no IntelliSense, uma API não funcionará para uma estrutura de destino especificada. Exemplo de texto: namespace System.Buffers, SharedUtils (netstandard2.0) - Não Disponível. Você pode usar a barra de navegação para mudar o contexto.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Confira também

- [Visão geral de segmentação de framework (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Estruturas de destino em projetos no estilo SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
