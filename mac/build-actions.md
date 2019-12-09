---
title: Ações de Build
description: Este artigo descreve as diferentes ações de build que podem ser usadas para projetos em C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714393"
---
# <a name="build-actions"></a>Ações de Build

Todos os arquivos em um projeto do Visual Studio para Mac têm uma ação de build. A ação de compilação controla o que acontece com o arquivo durante uma compilação. 

>[!NOTE]
>Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, consulte [ações de compilação](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Definir uma ação de build

Para definir uma ação de compilação para um arquivo em Visual Studio para Mac, você pode clicar com o botão direito do mouse em qualquer arquivo e navegar até a **ação de Build**, conforme ilustrado abaixo:

![Selecionando ação Compilar build no Gerenciador de Soluções](media/projects-and-solutions-image1.png)

As ações de compilação para esse arquivo serão mostradas no menu suspenso. 

## <a name="build-action-values"></a>Valores de ação de build

Algumas das ações comuns de compilação para projetos que você pode criar no Visual Studio para Mac incluem:

|Ação de compilação | Tipos de projeto | Descrição |
|--|--|--|
| **Compile** | qualquer | O arquivo é passado para o C# compilador como um arquivo de origem.|
| **Disputa** | .NET, Xamarin | Para projetos ASP.NET, esses arquivos são incluídos como parte do site quando ele for implantado. Para projetos Xamarin.iOS e Xamarin.Mac, eles estarão incluídos no lote de aplicativo.|
| **Embedded Resource** | .NET | O arquivo é passado para o C# compilador como um recurso a ser inserido no assembly. O [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), do namespace `System.Reflection`, pode ser usado para ler o arquivo do assembly.|
| **Nenhum** | qualquer | O arquivo não faz parte da compilação de nenhuma forma e é incluído no projeto para facilitar o acesso do IDE. Esse valor pode ser usado para arquivos de documentação como "Leiame", por exemplo.|

> [!NOTE]
> Ações adicionais de build podem ser definidas por tipos de projeto específicos, portanto, a lista de ações de build depende do tipo de projeto, e podem aparecer valores que não estão nessa lista.  

Projetos Xamarin.iOS têm a ação de build **BundleResource**, que adiciona o arquivo como parte do pacote de aplicativo. Informações sobre as ações de build específicas do Xamarin.Android podem ser encontradas no guia de [processo de build](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

Também é possível selecionar mais de um arquivo no Gerenciador de soluções, permitindo que você defina a ação de compilação para muitos arquivos ao mesmo tempo.

## <a name="see-also"></a>Consulte também

- [Ações de build (Visual Studio no Windows)](/visualstudio/ide/build-actions)