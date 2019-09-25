---
title: 'CA1707: Identificadores não devem conter sublinhados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adfa0ccd63d0433d367b0e7278693608bb83d685
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234266"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identificadores não devem conter sublinhados

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Categoria|Microsoft.Naming|
|Alteração significativa|Quebra-quando elevado em assemblies<br /><br /> Não separável-quando elevado em parâmetros de tipo|

## <a name="cause"></a>Causa

O nome de um identificador contém o caractere de sublinhado (\_).

## <a name="rule-description"></a>Descrição da regra

Por convenção, os nomes de identificador não contêm o caractere de\_sublinhado (). A regra verifica namespaces, tipos, membros e parâmetros.

As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Remova todos os caracteres de sublinhado do nome.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas

- [CA1709: Os identificadores devem estar em maiúsculas e minúsculas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Os identificadores devem ser diferentes em mais do que caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
