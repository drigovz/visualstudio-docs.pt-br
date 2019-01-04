---
title: Conjunto de regras de globalização para código gerenciado
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a0c0eb4edfb58d740692f2afff187659a665b234
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936978"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de regras de globalização para código gerenciado
Você pode usar as regras de globalização da Microsoft conjunto de regras para se concentrar em problemas que podem impedir que os dados em seu aplicativo apareça corretamente em diferentes idiomas, localidades e culturas. Você deve incluir essa regra definida se seu aplicativo for localizado, globalizado, ou ambos.

|Regra|Descrição|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Especificar MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar aceleradores duplicados|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Não embutir no código cadeias de caracteres específicas da localidade|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Não passar literais como parâmetros localizados|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Especificar CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Especificar IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Definir localidade para tipos de dados|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Especificar StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizar cadeias de caracteres em maiúsculas|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Usar StringComparison ordinal|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|