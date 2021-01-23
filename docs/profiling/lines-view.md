---
title: Exibição de Linhas | Microsoft Docs
description: Saiba como a exibição de linhas está disponível somente para dados do criador de perfil que foram coletados usando o método de amostragem.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac0d7785071e5f2928e7eabb4a29b1655b42c5ad
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721288"
---
# <a name="lines-view"></a>Exibição de linhas
A exibição de Linhas está disponível somente para dados de criador de perfil coletados por meio do método de amostragem. A exibição não está disponível para dados coletados por meio de instrumentação.

 Para dados de perfil de amostragem, as exibições de Linhas identificam a instrução em uma função que foi diretamente executada quando a amostra foi coletada. Para dados da memória do .NET, as exibições de Linhas identificam as instruções que alocam memória.

 Em um arquivo de origem, uma instrução pode abranger mais de uma linha em um arquivo de origem e uma única linha pode incluir mais de uma instrução.

 Uma instrução é identificada pelo seguinte:

- O arquivo de origem que contém a instrução da função.

- A função que contém a instrução.

- A linha de origem em que a instrução se inicia.

- O caractere na linha de origem em que a instrução se inicia.

- A linha de origem em que a instrução termina.

- O caractere na linha de origem em que a instrução termina.

## <a name="see-also"></a>Confira também
- [Exibição de linhas](../profiling/lines-view-sampling-data.md)
- [Exibição de linhas-amostragem](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Exibição de linhas](../profiling/lines-view-contention-data.md)
