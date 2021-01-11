---
title: Métricas de código-intervalo de índice de manutenção e significado
ms.date: 1/8/2021
description: Saiba mais sobre a métrica de intervalo de índice de manutenção para métricas de código no Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14bee6dcb522b7c1dd0475ca309b829a09c0d4ec
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069583"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Métricas de código-intervalo de índice de manutenção e significado

Pergunta: o índice de manutenção foi redefinido para estar entre 0 e 100. Como e por que isso foi feito?

A métrica originalmente foi calculada da seguinte maneira: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

O uso desta fórmula significava que ela foi enlinhada de 171 para um número negativo não associado.  Como o código tendiam em direção a 0, foi claramente difícil manter o código e a diferença entre o código em 0 e algum valor negativo não era útil.  Como resultado da diminuição da utilidade dos números negativos e de um desejo de manter a métrica o mais clara possível, decidimos tratar todos os 0 ou menos índices como 0 e, em seguida, trocar os 171 ou menos o intervalo de 0 a 100. Por esse motivo, a fórmula que usamos é:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Além disso, decidimos ser conservador com os limites.  O desejo era que, se o índice mostrasse vermelho, estaria dizendo um alto grau de confiança de que houve um problema com o código.  Isso nos forneceu os seguintes limites:

Para os limites, decidimos dividir este intervalo de 0-100 a 80-20 para manter o nível de ruído baixo e sinalizamos apenas um código suspeito. Utilizamos os seguintes limites:

- 0-9 = vermelho
- 10-19 = amarelo
- 20-100 = verde
