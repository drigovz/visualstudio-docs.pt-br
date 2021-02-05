---
title: Usar o MSBuild.exe para compilar destinos específicos em soluções
description: Saiba como usar MSBuild.exe linha de comando para criar destinos específicos de projetos específicos em soluções.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94fcd9e1ed16b86caf65b9c7fab44ba4f93b7a7a
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572896"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Como criar destinos específicos em soluções usando o MSBuild.exe

Use o *MSBuild.exe* para criar destinos específicos de projetos específicos em uma solução.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Para criar um destino específico de um projeto específico em uma solução

1. Na linha de comando, digite `MSBuild.exe <SolutionName>.sln`, em que `<SolutionName>` corresponde ao nome de arquivo da solução que contém o destino que você deseja executar.

2. Especifique o destino após a `-target:` opção no formato \<ProjectName> : \<TargetName> . Se o nome do projeto contiver algum dos caracteres `%`, `$`, `@`, `;`, `.`, `(`, `)` ou `'`, substitua-os por um `_` no nome de destino especificado.

## <a name="example"></a>Exemplo

 O exemplo a seguir executa o destino `Rebuild` do projeto `NotInSlnFolder` e, em seguida, executa o destino `Clean` do projeto `InSolutionFolder`, que está localizado na pasta de solução *NewFolder*.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Solução de problemas

Se quiser examinar as opções disponíveis para você, será possível usar uma opção de depuração fornecida pelo MSBuild para fazer isso. Defina a variável de ambiente `MSBUILDEMITSOLUTION=1` e crie sua solução. Isso produzirá um arquivo MSBuild chamado *\<SolutionName> . sln. metaproj* que mostra a exibição interna do MSBuild da solução no momento da compilação. Você pode inspecionar esta exibição para determinar quais destinos estão disponíveis para build.

Não compile com essa variável de ambiente definida a menos que precise dessa exibição interna. Essa configuração pode causar problemas ao criar projetos na sua solução. Em vez disso, procure no [log binário](obtaining-build-logs-with-msbuild.md#save-a-binary-log) .

## <a name="see-also"></a>Confira também

- [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
