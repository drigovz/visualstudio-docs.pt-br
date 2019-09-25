---
title: 'CA1823: Evitar campos particulares não utilizados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f0aa23ff93e193ee06509c1cb635404ec827793
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233356"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitar campos particulares não utilizados

|||
|-|-|
|NomeDoTipo|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Essa regra é relatada quando um campo privado em seu código existe, mas não é usado por nenhum caminho de código.

## <a name="rule-description"></a>Descrição da regra
Foram detectados campos particulares que aparentemente não são acessados no assembly.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova o campo ou adicione o código que o utiliza.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra.

## <a name="related-rules"></a>Regras relacionadas
[CA1812: Evitar classes internas não instanciadas](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)

[CA1811: Evitar código particular não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)