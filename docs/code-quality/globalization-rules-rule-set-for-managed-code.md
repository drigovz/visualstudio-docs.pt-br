---
title: Conjunto de regras de globalização para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ffba6b69e1f67b369f3d99c1b54a88448df8a41b
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69584986"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de regras de globalização para código gerenciado

Use o conjunto de regras Microsoft Globalization Rules para se concentrar em problemas que podem impedir que os dados em seu aplicativo sejam exibidos corretamente em diferentes idiomas, localidades e culturas. Você deve incluir esse conjunto de regras se seu aplicativo for localizado, globalizado ou ambos.

|Regra|Descrição|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Especificar MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar aceleradores duplicados|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Não codificar Cadeias de caracteres específicas de localidade|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Não passar literais como parâmetros localizados|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Especificar CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Especificar IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Definir localidade para tipos de dados|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Especificar StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizar cadeias de caracteres em maiúsculas|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Usar StringComparison ordinal|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|