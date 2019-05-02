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
ms.openlocfilehash: 2c1d2aa6f0889216b39b891b042989f1c8c69692
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545978"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Identificadores não devem ter um prefixo incorreto

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um identificador tem um prefixo incorreto.

## <a name="rule-description"></a>Descrição da regra
 Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.

 Nomes de tipo não têm um prefixo específico e não devem ser prefixados com um 'c'. Esta regra relata violações para nomes de tipo como 'CMyClass' e não relata violações para nomes de tipo como 'Cache'.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Essa consistência reduz a curva de aprendizado necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Remova o prefixo do identificador.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1715: Os identificadores devem ter prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)