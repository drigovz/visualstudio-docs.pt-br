---
title: 'CA1034: os tipos aninhados não devem ser visíveis'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0726b6f02de37c9a5537db59b264802c3dad9a07
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440869"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: os tipos aninhados não devem ser visíveis

|||
|-|-|
|NomeDoTipo|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Categoria|Microsoft. Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo visível externamente contém uma declaração de tipo visível externamente. Enumerações aninhadas e tipos protegidos são isentos dessa regra.

## <a name="rule-description"></a>Descrição da regra
Um tipo aninhado é um tipo declarado dentro do escopo de outro tipo. Tipos aninhados são úteis para encapsular detalhes de implementação privada do tipo recipiente. Usados para essa finalidade, os tipos aninhados não devem ser visíveis externamente.

Não use tipos aninhados externamente visíveis para agrupamento lógico ou para evitar colisões de nome; em vez disso, use namespaces.

Os tipos aninhados incluem a noção de acessibilidade de membro, que alguns programadores não entendem claramente.

Os tipos protegidos podem ser usados em subclasses e em tipos aninhados em cenários de personalização prévia.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Se você não pretender que o tipo aninhado fique visível externamente, altere a acessibilidade do tipo. Caso contrário, remova o tipo aninhado de seu pai. Se a finalidade do aninhamento for categorizar o tipo aninhado, use um namespace para criar a hierarquia em vez disso.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola a regra.

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]
