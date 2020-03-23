---
title: Uso de memória com eficiência ao compilar projetos grandes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f40f2713d93e4f1ad9755efaea2f8fba5f0bda94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631309"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Usar memória com eficiência ao compilar projetos grandes

Projetos grandes geralmente contêm diversos subprojetos e outras dependências que podem consumir muita memória do sistema no momento da compilação. Quando a memória disponível no sistema é reduzida, o desempenho do sistema também pode diminuir. Versões mais antigas de projetos MSBuild permaneceram na memória. A versão 3.5 removeu versões mais antigas de projetos, mas mantinha resultados da compilação em um cache para recuperação posterior.

 A versão 4.0 manipula esse gerenciamento de memória automaticamente, evitando que projetos usem propriedades como `UnloadProjectsOnCompletion` e `UseResultsCache`.

### <a name="see-also"></a>Confira também

- [Construa vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
