---
title: Filtros de solução no MSBuild
description: Explica filtros de solução e mostra como criar um arquivo de filtro de solução com o MSBuild.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 998103828d20827e8a1d99e0cc34d7f9beb6bd7c
ms.sourcegitcommit: 9179c33a78c2ac690ce908d7c73eef50b6e367f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87401022"
---
# <a name="solution-filters-in-msbuild"></a>Filtros de solução no MSBuild

Arquivos de filtro de solução são arquivos JSON com a extensão *. slnf* que indicam quais projetos devem ser compilados ou carregados de todos os projetos em uma solução. A partir do MSBuild 16,7, você pode invocar o MSBuild no arquivo de filtro da solução para criar a solução com a filtragem habilitada. 

> [!NOTE]
> O arquivo de filtro de solução reduz o conjunto de projetos que serão carregados ou compilados e simplifica o formato. O arquivo de solução ainda é necessário.

## <a name="build-a-solution-filter-from-the-command-line"></a>Criar um filtro de solução na linha de comando

A criação de um arquivo de filtro de solução a partir da linha de comando usa exatamente a mesma sintaxe que a criação de um arquivo de solução. Especifique o arquivo de filtro da solução em vez da solução a ser criada com a filtragem habilitada, da seguinte maneira:

```console
msbuild [options] solutionFilterFile.slnf
```

Você também pode acrescentar opções e propriedades extras normalmente. Consulte [referência de linha de comando do MSBuild](msbuild-command-line-reference.md). Esse comando cria os projetos filtrados e quaisquer projetos dos quais eles dependem. Ao criar um filtro de solução na linha de comando, o MSBuild segue automaticamente as dependências. Ele cria um projeto se ele for especificado no filtro ou referenciado por um projeto criado.

## <a name="solution-filter-files"></a>Arquivos do filtro de solução

Você pode usar o Visual Studio para trabalhar com arquivos de filtro de solução. Abrir um filtro de solução no Visual Studio exibe os projetos descarregados, bem como os projetos carregados e oferece a opção de carregar mais projetos para selecioná-los para criação. Você pode carregar todos os projetos dos quais os projetos iniciais dependem para compilar também, mas isso não é necessário. Consulte [soluções filtradas](../ide/filtered-solutions.md).

O filtro de solução não precisa estar na mesma pasta que a solução. O caminho para o arquivo de solução é relativo ao local do arquivo de filtro de solução, mas os caminhos para cada projeto são relativos ao próprio arquivo de solução e devem corresponder aos caminhos de projeto no arquivo de solução. O exemplo a seguir demonstra o uso de caminhos relativos:

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

As barras invertidas em caminhos devem ser duplicadas, pois elas têm escape.

## <a name="example"></a>Exemplo

Aqui está um exemplo de uma solução filtrada no Visual Studio:

![Captura de tela da solução filtrada no Visual Studio](media/solution-with-filter.png)

Nesta solução, ClassLibrary1 é usado pelo projecta e ProjectB e, portanto, ClassLibrary1 é listado como uma referência de projeto.

Este é o arquivo de filtro de solução que o Visual Studio gera:

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

Neste exemplo, quando você cria com filtragem habilitada (usando o comando `MSBuild [options] MyFilter.slnf` ), o MSBuild cria MyApplication e projecta porque eles estão explicitamente listados no arquivo de filtro da solução. Como parte da criação do projecta, o MSBuild compila ClassLibrary1 porque o projecta depende dele.  ProjectB não foi compilado. (Essa discussão pressupõe uma compilação limpa. Se os projetos foram criados anteriormente, as regras usuais se aplicam para ignorar projetos que já estão atualizados.

## <a name="see-also"></a>Confira também

- [Soluções filtradas](../ide/filtered-solutions.md)
- [Referência de linha de comando do MSBuild](msbuild-command-line-reference.md)
