---
title: Uso de memória com eficiência ao compilar projetos grandes | Microsoft Docs
description: Saiba como o MSBuild gerencia a memória automaticamente, como descarregar versões mais antigas e recuperar caches ao criar projetos grandes.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 61bfa09bf91b49c163e47bbf71c0d192b6950160
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047605"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Usar memória com eficiência ao compilar projetos grandes

Projetos grandes geralmente contêm diversos subprojetos e outras dependências que podem consumir muita memória do sistema no momento da compilação. Quando a memória disponível no sistema é reduzida, o desempenho do sistema também pode diminuir. As versões mais antigas dos projetos do MSBuild permaneceram na memória. A versão 3.5 removeu versões mais antigas de projetos, mas mantinha resultados da compilação em um cache para recuperação posterior.

 A versão 4.0 manipula esse gerenciamento de memória automaticamente, evitando que projetos usem propriedades como `UnloadProjectsOnCompletion` e `UseResultsCache`.

### <a name="see-also"></a>Veja também

- [Crie vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
