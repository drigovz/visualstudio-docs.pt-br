---
title: Ações de Build
description: Este artigo descreve as diferentes ações de build que podem ser usadas para projetos em C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714393"
---
# <a name="build-actions"></a>Ações de Build

Todos os arquivos em um projeto do Visual Studio para Mac têm uma ação de build. A ação de compilação controla o que acontece com o arquivo durante uma compilação. 

>[!NOTE]
>Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, consulte [Construir ações](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Definir uma ação de build

Para definir uma ação de compilação para um arquivo no Visual Studio para Mac, você pode clicar com o botão direito do mouse em qualquer arquivo e navegação para **Build Action,** conforme ilustrado abaixo:

![Selecionando ação Compilar build no Gerenciador de Soluções](media/projects-and-solutions-image1.png)

As ações de construção deste arquivo serão mostradas no menu flyout. 

## <a name="build-action-values"></a>Valores de ação de build

Algumas das ações comuns de construção para projetos que você pode construir no Visual Studio para Mac incluem:

|Criar ação | Tipos de projeto | Descrição |
|--|--|--|
| **Compilar** | any | O arquivo é passado para o compilador C# como um arquivo de origem.|
| **Conteúdo** | .NET, Xamarin | Para projetos ASP.NET, esses arquivos são incluídos como parte do site quando ele for implantado. Para projetos Xamarin.iOS e Xamarin.Mac, eles estarão incluídos no lote de aplicativo.|
| **Embedded Resource** | .NET | O arquivo é passado para o compilador C# como um recurso a ser incorporado na montagem. O [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), do namespace `System.Reflection`, pode ser usado para ler o arquivo do assembly.|
| **Nenhum** | any | O arquivo não faz parte da compilação de forma alguma e está incluído no projeto para fácil acesso do IDE. Esse valor pode ser usado para arquivos de documentação como "Leiame", por exemplo.|

> [!NOTE]
> Ações adicionais de build podem ser definidas por tipos de projeto específicos, portanto, a lista de ações de build depende do tipo de projeto, e podem aparecer valores que não estão nessa lista.  

Projetos Xamarin.iOS têm a ação de build **BundleResource**, que adiciona o arquivo como parte do pacote de aplicativo. Informações sobre as ações de build específicas do Xamarin.Android podem ser encontradas no guia de [processo de build](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

Também é possível selecionar mais de um arquivo no explorador de soluções, permitindo que você defina a ação de compilação para muitos arquivos ao mesmo tempo.

## <a name="see-also"></a>Confira também

- [Ações de build (Visual Studio no Windows)](/visualstudio/ide/build-actions)