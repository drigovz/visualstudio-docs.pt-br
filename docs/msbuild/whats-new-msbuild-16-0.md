---
title: O que há &apos; de novo no MSBuild 16,0 | Microsoft Docs
description: Saiba mais sobre os recursos e as propriedades alterados e atualizados para MSBuild 16,0 e link para notas de versão.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: a4e0079fa301d751962a945a0bf8348ffd3c359d
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047795"
---
# <a name="whats-new-in-msbuild-160"></a>Novidades no MSBuild 16.0

Este artigo descreve os recursos e as propriedades atualizadas no MSBuild 16.0. Para obter as notas de versão detalhadas, consulte [ MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Caminho alterado

 O MSBuild é instalado na pasta *\* em cada versão do Visual Studio, e os executáveis estão na subpasta *\Bin* . Por exemplo, o caminho para *MSBuild.exe* instalado com o visual Studio 2019 Community é *C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* você também pode usar o seguinte módulo do PowerShell para localizar o MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Propriedades alteradas

 As propriedades do MSBuild a seguir foram atualizadas devido ao novo número de versão.

- A `MSBuildToolsVersion` desta versão das ferramentas é “Atual”. A versão do assembly é a mesma do Visual Studio 2017, que é 15.1.0.0.

- A `VisualStudioVersion` desta versão das ferramentas é "16.0"

## <a name="updates"></a>Atualizações

O MSBuild (e o Visual Studio) agora destina-se ao .NET Framework 4.7.2. Se você quiser usar os novos recursos de API do MSBuild, deverá atualizar também o seu assembly, mas o código existente continuará a funcionar.

## <a name="see-also"></a>Veja também

- [MSBuild](../msbuild/msbuild.md)
