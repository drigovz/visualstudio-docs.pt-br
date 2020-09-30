---
title: Depuração em pacotes NuGet com o link de origem
description: Este artigo descreve o recurso de link de origem no Visual Studio para Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583912"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Depuração em pacotes NuGet com o link de origem

A tecnologia de link de origem permite a depuração de código-fonte de assemblies .NET do NuGet que são fornecidos. PDBs com links para arquivos de origem. O link de origem é executado quando os desenvolvedores criam seu pacote NuGet e inserem metadados de controle do código-fonte dentro de assemblies e do pacote. Quando o link de origem estiver habilitado no Visual Studio para Mac, o IDE detectará se os arquivos de origem estão disponíveis para os pacotes instalados. Visual Studio para Mac, em seguida, oferecerá baixá-los, o que permitirá que você percorra o código do pacote. O link de origem também funciona com código de biblioteca de classes base mono para projetos do Xamarin, permitindo que você entre .NET Framework código também. O Source Link fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.

> [!NOTE]
> Atualmente, o Visual Studio para Mac não dá suporte a servidores de símbolo. Por isso, não há suporte para o link de origem com metadados hospedados em servidores de símbolos.

## <a name="enable-source-link"></a>Habilitar link de origem

Para habilitar o link de origem em Visual Studio para Mac, navegue até **Visual Studio > preferências... > projetos > depurador** e certifique-se de que a caixa de seleção **etapa em código externo** esteja marcada.

![Captura de tela da caixa de diálogo Preferências mostrando a etapa em código externo](media/source-link1.png)

Você pode alterar a configuração em **baixar código externo** para se adequar às suas preferências:
* Ask: Visual Studio para Mac solicitará que você baixe o código externo
* Sempre: Visual Studio para Mac baixará o código externo automaticamente
* Nunca: Visual Studio para Mac não baixará o código externo relacionado

Por padrão, **Ask** está selecionado. Você receberá o seguinte prompt quando o código externo for encontrado para um pacote NuGet:

![Captura de tela do prompt que aparece quando o código externo é encontrado para um pacote NuGet](media/source-link2.png)


## <a name="see-also"></a>Confira também

- O [repositório GitHub do link de origem](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Documentação do .net](/dotnet/standard/library-guidance/sourcelink) no link de origem e para obter mais informações sobre como adicionar suporte a links de origem a pacotes