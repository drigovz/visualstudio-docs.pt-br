---
title: Regra de regras de globalização definida para código gerenciado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1630769b5150d9cef7b00e575ac9c555f5bc5be1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667614"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de regras de globalização para código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar o conjunto de regras do Microsoft Globalization Rules para se concentrar em problemas que podem impedir que os dados em seu aplicativo sejam exibidos corretamente em diferentes idiomas, localidades e culturas. Você deve incluir esse conjunto de regras se seu aplicativo for localizado, globalizado ou ambos.

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
