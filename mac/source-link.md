---
title: Depuração em pacotes NuGet com Link de Origem
description: Este artigo descreve o recurso Source Link no Visual Studio for Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451485"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Depuração em pacotes NuGet com Link de Origem

A tecnologia Source Link permite a depuração do código-fonte dos conjuntos .NET do NuGet nesse navio . PDBs com links para arquivos de origem. O Source Link é executado quando os desenvolvedores criam seu pacote NuGet e incorporam metadados de controle de origem dentro de conjuntos e do pacote. Quando o Source Link estiver ativado no Visual Studio for Mac, o IDE detectará se os arquivos de origem estão disponíveis para pacotes instalados. Visual Studio para Mac, então, oferecerá para baixá-los, o que permitirá que você passe pelo código do pacote. O Source Link também funciona com o código mono base class library para projetos Xamarin, permitindo que você também entre no código .NET Framework. O Source Link fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.

> [!NOTE]
> Visual Studio for Mac não suporta atualmente servidores símbolo. Por causa disso, o Source Link com metadados hospedados em servidores símbolo não é suportado.

## <a name="enable-source-link"></a>Habilitar link de origem

Para habilitar o Source Link no Visual Studio para Mac, navegue até **o Visual Studio > Preferências... > Projetos > Debugger** e certifique-se de que a caixa de seleção de código externo Step **in.**

![Captura de tela de diálogo de preferências mostrando Passo na caixa de seleção de código externo](media/source-link1.png)

Você pode alterar a configuração em **Download Código Externo** para atender às suas preferências:
* Pergunte: Visual Studio para Mac vai solicitar que você baixe o código externo
* Sempre: Visual Studio para Mac baixará o código externo automaticamente
* Nunca: Visual Studio para Mac não baixará o código externo relacionado

Por padrão, **Ask** é selecionado. Você receberá o seguinte prompt quando o código externo for encontrado para um pacote NuGet:

![Captura de tela do prompt que aparece quando o código externo é encontrado para um pacote NuGet](media/source-link2.png)


## <a name="see-also"></a>Confira também

- O [repositório Source Link GitHub](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Documentação .NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) no Source Link e para obter mais informações sobre como adicionar suporte ao Source Link a pacotes
