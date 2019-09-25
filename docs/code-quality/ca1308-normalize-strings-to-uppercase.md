---
title: 'CA1308: Normalizar cadeias de caracteres em maiúsculas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c33f4b0b55728d659c34e0ffc8723f555a6d074d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234924"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizar cadeias de caracteres em maiúsculas

|||
|-|-|
|NomeDoTipo|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Categoria|Microsoft. Globalization|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Uma operação normaliza uma cadeia de caracteres para minúsculas.

## <a name="rule-description"></a>Descrição da regra
As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres, quando são convertidos em minúsculas, não pode fazer uma viagem de ida e volta. Fazer uma viagem de ida e volta significa converter os caracteres de uma localidade em outra localidade que representa dados de caracteres de forma diferente e, em seguida, recuperar com precisão os caracteres originais dos caracteres convertidos.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Altere as operações que convertem cadeias de caracteres em minúsculas para que as cadeias de caracteres sejam convertidas em maiúsculas. Por exemplo, altere `String.ToLower(CultureInfo.InvariantCulture)` para `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir uma mensagem de aviso quando você não está tomando decisão de segurança com base no resultado (por exemplo, quando você a exibe na interface do usuário).

## <a name="see-also"></a>Consulte também
[Avisos de globalização](../code-quality/globalization-warnings.md)