---
title: Introdução com devinit
description: Guia de introdução para devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 62c31dcb72735304f7b28e7dfd817f6647187bc9
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022625"
---
# <a name="getting-started-with-devinit"></a>Introdução com devinit

## <a name="step-1-get-devinit"></a>Etapa 1: obter devinit

Atualmente, o devinit só está disponível como parte do GitHub Codespaces ao usar o Visual Studio e é acessível a partir do terminal integrado no Visual Studio. No futuro, o devinit estará disponível como parte do Visual Studio.

## <a name="step-2-define-your-environment"></a>Etapa 2: definir seu ambiente

A etapa mais importante é definir o ambiente de ' desenvolvedor ' em um [ _.devinit.jsno_ arquivo](devinit-json.md). Esse arquivo será usado pelo devinit para criar seu ambiente quando você executar o `devinit init` .

Para esta etapa, pense nas instruções que você daria para que alguém coloque em funcionamento com um repositório de projeto. Por exemplo, eles precisam ter o SQL instalado? Uma versão específica do .NET Core? diante. Em seguida, para cada uma dessas dependências, procure uma ferramenta devinit correspondente na [lista de ferramentas](devinit-tool-list.md) e adicione-a à.devinit.jsdo repositório _ no_ arquivo.

## <a name="step-3-enjoy"></a>Etapa 3: Aproveite!

Agora, tudo o que alguém precisa fazer depois de clonar seu repositório é executado `devinit init` .

```console
> devinit init
```

Se você estiver usando o [GitHub Codespaces](https://github.com/features/codespaces), poderá configurar `devinit init` para ser executado automaticamente quando o codespace for provisionado. Para saber mais, confira a [documentação do devinit e do GitHub Codespaces](devinit-and-codespaces.md).