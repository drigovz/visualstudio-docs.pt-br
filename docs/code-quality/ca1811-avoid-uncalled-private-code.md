---
title: 'CA1811: Evitar código particular não chamado'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a7542499eceeccbd62ce327b386dc099b726b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233615"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Evitar código particular não chamado

|||
|-|-|
|NomeDoTipo|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um membro privado ou interno (no nível do assembly) não tem chamadores no assembly, não é invocado pelo Common Language Runtime e não é invocado por um delegado. Os seguintes membros não são verificados por esta regra:

- Membros de interface explícitos.

- Construtores estáticos.

- Construtores de serialização.

- Métodos marcados com <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

- Membros que são substituições.

## <a name="rule-description"></a>Descrição da regra
Essa regra pode relatar falsos positivos se ocorrerem pontos de entrada que não estão identificados atualmente pela lógica da regra. Além disso, um compilador pode emitir código não chamável em um assembly.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova o código não chamável ou adicione o código que o chama.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra.

## <a name="related-rules"></a>Regras relacionadas
[CA1812: Evitar classes internas não instanciadas](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)