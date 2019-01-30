---
title: Uso de memória com eficiência ao compilar projetos grandes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d18f78a0ceec7b79388f53f83909e4dcbcf3b86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923527"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Usar memória com eficiência ao compilar projetos grandes
Projetos grandes geralmente contêm diversos subprojetos e outras dependências que podem consumir muita memória do sistema no momento da compilação. Quando a memória disponível no sistema é reduzida, o desempenho do sistema também pode diminuir. As versões mais antigas de projetos do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] permaneceram na memória. A versão 3.5 removeu versões mais antigas de projetos, mas mantinha resultados da compilação em um cache para recuperação posterior.  
  
 A versão 4.0 manipula esse gerenciamento de memória automaticamente, evitando que projetos usem propriedades como `UnloadProjectsOnCompletion` e `UseResultsCache`.  
  
### <a name="see-also"></a>Consulte também  
 [Criar vários projetos paralelamente](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)