---
title: Conjunto de regras de globalização para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2af6126c751d03968dc7ecd87693e3546376c12a
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509855"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de regras de globalização para código gerenciado

Use o conjunto de regras Microsoft Globalization Rules para se concentrar em problemas que podem impedir que os dados em seu aplicativo sejam exibidos corretamente em diferentes idiomas, localidades e culturas. Você deve incluir esse conjunto de regras se seu aplicativo for localizado, globalizado ou ambos.

|Regra|Descrição|
|----------|-----------------|
|[CA1303](../code-quality/ca1303.md)|Não passar literais como parâmetros localizados|
|[CA1304](../code-quality/ca1304.md)|Especificar CultureInfo|
|[CA1305](../code-quality/ca1305.md)|Especificar IFormatProvider|
|[CA1307](../code-quality/ca1307.md)|Especificar StringComparison para fins de clareza|
|[CA1308](../code-quality/ca1308.md)|Normalizar cadeias de caracteres em maiúsculas|
|[CA1309](../code-quality/ca1309.md)|Usar StringComparison ordinal|
|[CA1310](../code-quality/ca1310.md)|Especificar StringComparison para exatidão|
|[CA2101](../code-quality/ca2101.md)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|
