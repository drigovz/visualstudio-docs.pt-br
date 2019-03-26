---
title: Novidades no MSBuild 16.0 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9fb23c8a48493056c9a37f510cefea3cc3374095
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57987030"
---
# <a name="whats-new-in-msbuild-160"></a>Novidades no MSBuild 16.0

Este artigo descreve os recursos e as propriedades atualizadas no MSBuild 16.0. Nas notas sobre a versão detalhadas (somente rascunho), consulte [ MSBuild 16.0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

## <a name="changed-path"></a>Caminho alterado

 Agora o MSBuild é instalado na pasta *\Current* em cada versão do Visual Studio. Por exemplo, *C:\Arquivos de Programas (x86) \Microsoft Visual Studio\Current\Enterprise\MSBuild*. Você também pode usar o seguinte módulo do PowerShell para localizar o MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Propriedades alteradas

 As propriedades do MSBuild a seguir foram atualizadas devido ao novo número de versão.

- A `MSBuildToolsVersion` desta versão das ferramentas é “Atual”. A versão do assembly é a mesma do Visual Studio 2017, que é 15.1.0.0.

- A `VisualStudioVersion` desta versão das ferramentas é "16.0"

## <a name="updates"></a>Atualizações

O MSBuild (e o Visual Studio) agora destina-se ao .NET Framework 4.7.2. Se você quiser usar os novos recursos de API do MSBuild, deverá atualizar também o seu assembly, mas o código existente continuará a funcionar.

## <a name="see-also"></a>Consulte também
- [MSBuild](../msbuild/msbuild.md)
