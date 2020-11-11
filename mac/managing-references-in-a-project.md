---
title: Gerenciando referências em um projeto
description: Este artigo descreve como gerenciar referências em um projeto no Visual Studio para Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 41d49fe6b23818f3cb9de8dec72462d4b2029bb6
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493511"
---
# <a name="managing-references-in-a-project"></a>Gerenciando referências em um projeto

O Visual Studio para Mac fornece dois meios de acrescentar referências adicionais ao seu projeto:

![Referências de Projeto](media/projects-and-solutions-image10.png)

Eles são:

* Referências
* Pacotes NuGet (adicionados por meio da pasta pacotes)

Além disso, as referências Web e nativas também podem ser adicionadas a qualquer projeto.

## <a name="assembly-references"></a>Referências de assembly

Cada estrutura do Xamarin é fornecida com diversos assemblies. Nem todos esses pacotes de assembly são referenciados no seu projeto por padrão.

Para editar pacotes que são referenciados no seu projeto, use a caixa de diálogo **Editar Referências** , que é exibida clicando duas vezes na pasta Referências ou selecionando **Editar Referências** nas ações do menu de contexto:

![Caixa de diálogo Referências do assembly](media/projects-and-solutions-image11.png)

Para obter informações sobre os assemblies disponíveis para cada estrutura d Xamarin, consulte o guia [Assemblies disponíveis](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet é o gerenciador de pacote mais popular para desenvolvimento .NET. O NuGet do Visual Studio para Mac permite que você pesquise pacotes para adicionar ao seu projeto.

Para fazer isso, clique com o botão direito do mouse na pasta do **pacote** na janela da solução e selecione Adicionar pacotes.

Mais informações sobre como usar um pacote NuGet são fornecidas no passo a passo [Incluindo pacote NuGet no seu projeto](nuget-walkthrough.md).

## <a name="see-also"></a>Confira também

- [Gerenciar referências (Visual Studio no Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Adicionando referências usando o NuGet versus um SDK de extensão (Visual Studio no Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)