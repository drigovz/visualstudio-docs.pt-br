---
title: 'CA1722: Identificadores não devem ter um prefixo incorreto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb41f2ad4548933d10137e7f72cae59643d33043
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233885"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Identificadores não devem ter um prefixo incorreto

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Categoria|Microsoft.Naming|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um identificador tem um prefixo incorreto.

## <a name="rule-description"></a>Descrição da regra
Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.

Os nomes de tipo não têm um prefixo específico e não devem ser prefixados com um ' C'. Essa regra relata violações para nomes de tipo, como ' CMyClass ', e não relata violações para nomes de tipo, como ' cache '.

As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Essa consistência reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Remova o prefixo do identificador.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
[CA1715: Os identificadores devem ter o prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)