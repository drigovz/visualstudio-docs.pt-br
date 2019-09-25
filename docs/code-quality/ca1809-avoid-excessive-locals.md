---
title: 'CA1809: Evitar locais excessivos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89d6ee4d1a53f63cffb31439a124d3d9358e976f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233641"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitar locais excessivos

|||
|-|-|
|NomeDoTipo|AvoidExcessiveLocals|
|CheckId|CA1809|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um membro contém mais de 64 variáveis locais, algumas das quais podem ser geradas pelo compilador.

## <a name="rule-description"></a>Descrição da regra
Uma otimização de desempenho comum é armazenar um valor em um registro de processador em vez de na memória, que é conhecido como *registrar* o valor. O Common Language Runtime considera até 64 variáveis locais para o registro. As variáveis que não são registradas são colocadas na pilha e devem ser movidas para um registro antes da manipulação. Para permitir a chance de que todas as variáveis locais sejam registradas, limite o número de variáveis locais a 64.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, refatore a implementação para usar no máximo 64 variáveis locais.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra ou desabilitar a regra, se o desempenho não for um problema.

## <a name="related-rules"></a>Regras relacionadas
[CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)