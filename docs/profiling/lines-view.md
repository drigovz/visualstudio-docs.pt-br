---
title: Exibição de Linhas | Microsoft Docs
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
ms.workload:
- multiple
ms.openlocfilehash: 905979e0bc563e7525f1385a484e9b44b523a1f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613980"
---
# <a name="lines-view"></a>Exibição de linhas
A exibição de Linhas está disponível somente para dados de criador de perfil coletados por meio do método de amostragem. A exibição não está disponível para dados coletados por meio de instrumentação.

 Para dados de perfil de amostragem, as exibições de Linhas identificam a instrução em uma função que foi diretamente executada quando a amostra foi coletada. Para dados da memória do .NET, as exibições de Linhas identificam as instruções que alocam memória.

 Em um arquivo de origem, uma instrução pode abranger mais de uma linha em um arquivo de origem e uma única linha pode incluir mais de uma instrução.

 Uma instrução é identificada pelo seguinte:

-   O arquivo de origem que contém a instrução da função.

-   A função que contém a instrução.

-   A linha de origem em que a instrução se inicia.

-   O caractere na linha de origem em que a instrução se inicia.

-   A linha de origem em que a instrução termina.

-   O caractere na linha de origem em que a instrução termina.

## <a name="see-also"></a>Consulte também
- [Exibição de Linhas](../profiling/lines-view-sampling-data.md)
- [Exibição de linhas – amostragem](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Exibição de Linhas](../profiling/lines-view-contention-data.md)