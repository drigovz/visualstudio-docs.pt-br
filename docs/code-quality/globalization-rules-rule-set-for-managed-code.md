---
title: Conjunto de regras de globalização para código gerenciado
ms.date: 11/04/2016
description: Saiba mais sobre o conjunto de regras de regras de globalização no Visual Studio, que se concentra em problemas relacionados a linguagens, localidades e culturas. Consulte descrições de regra.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0bf96c8e4140e5b491624d6750b498a26726761c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348873"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de regras de globalização para código gerenciado

Use o conjunto de regras Microsoft Globalization Rules para se concentrar em problemas que podem impedir que os dados em seu aplicativo sejam exibidos corretamente em diferentes idiomas, localidades e culturas. Você deve incluir esse conjunto de regras se seu aplicativo for localizado, globalizado ou ambos.

|Regra|Descrição|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Não passar literais como parâmetros localizados|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|Especificar CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|Especificar IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Especificar StringComparison para fins de clareza|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizar cadeias de caracteres em maiúsculas|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Usar StringComparison ordinal|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Especificar StringComparison para exatidão|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|
