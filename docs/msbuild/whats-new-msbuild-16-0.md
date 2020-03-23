---
title: Novidades no MSBuild 16.0 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 69c576f34b73ec99edd231d39e8bfa8ea661f2ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652801"
---
# <a name="whats-new-in-msbuild-160"></a>Novidades no MSBuild 16.0

Este artigo descreve os recursos e as propriedades atualizadas no MSBuild 16.0. Para obter as notas detalhadas de versão, consulte [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Caminho alterado

 O MSBuild está instalado na pasta *\Atual* em cada versão do Visual Studio, e os executáveis estão na subpasta *\Bin.* Por exemplo, o caminho para *o MSBuild.exe* instalado com o Visual Studio 2019 Community é *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* Você também pode usar o seguinte módulo PowerShell para localizar o MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Propriedades alteradas

 As propriedades do MSBuild a seguir foram atualizadas devido ao novo número de versão.

- A `MSBuildToolsVersion` desta versão das ferramentas é “Atual”. A versão do assembly é a mesma do Visual Studio 2017, que é 15.1.0.0.

- A `VisualStudioVersion` desta versão das ferramentas é "16.0"

## <a name="updates"></a>Atualizações

O MSBuild (e o Visual Studio) agora destina-se ao .NET Framework 4.7.2. Se você quiser usar os novos recursos de API do MSBuild, deverá atualizar também o seu assembly, mas o código existente continuará a funcionar.

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)
