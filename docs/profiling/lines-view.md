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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 25dbb0beb600f7f043ae006e09ac48b9b64d613b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773975"
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

## <a name="see-also"></a>Consulte também
- [Exibição de Linhas](../profiling/lines-view-sampling-data.md)
- [Exibição de linhas – amostragem](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Exibição de Linhas](../profiling/lines-view-contention-data.md)
