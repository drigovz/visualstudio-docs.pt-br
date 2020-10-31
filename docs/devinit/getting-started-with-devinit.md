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
ms.openlocfilehash: ae274e460f4404efa92c4cf3785a3c2e41fd9691
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134073"
---
# <a name="getting-started-with-devinit"></a>Introdução com devinit

## <a name="step-1-get-devinit"></a>Etapa 1: obter devinit

Atualmente, o devinit só está disponível como parte do GitHub Codespaces ao usar o Visual Studio e é acessível a partir do terminal integrado no Visual Studio. No futuro, o devinit estará disponível como parte do Visual Studio.

## <a name="step-2-define-your-environment"></a>Etapa 2: definir seu ambiente

A etapa mais importante é definir o ambiente de ' desenvolvedor ' em um [ _.devinit.jsno_ arquivo](devinit-json.md). Esse arquivo será usado pelo devinit para criar seu ambiente quando você executar o `devinit init` .

Para esta etapa, pense nas instruções que você daria para que alguém coloque em funcionamento com um repositório de projeto. Por exemplo, eles precisam ter o SQL instalado? Uma versão específica do .NET Core? diante. Em seguida, para cada uma dessas dependências, procure uma ferramenta devinit correspondente na [lista de ferramentas](devinit-tool-list.md) e adicione-a à.devinit.jsdo repositório _no_ arquivo.

## <a name="step-3-enjoy"></a>Etapa 3: Aproveite!

Agora, tudo o que alguém precisa fazer depois de clonar seu repositório é executado `devinit init` .

```console
devinit init
```

Se você estiver usando o [GitHub Codespaces](https://github.com/features/codespaces), poderá configurar `devinit init` para ser executado automaticamente quando o codespace for provisionado. Para saber mais, confira a [documentação do devinit e do GitHub Codespaces](devinit-and-codespaces.md).
