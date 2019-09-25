---
title: 'CA1724: Nomes de tipos não devem corresponder a namespaces'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3554a352cb1c32879397e91dba3ce53f31a14bd0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233851"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Nomes de tipos não devem corresponder a namespaces

|||
|-|-|
|NomeDoTipo|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Categoria|Microsoft.Naming|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um nome de tipo corresponde a um nome de namespace referenciado que tem um ou mais tipos visíveis externamente. A comparação de nomes não diferencia maiúsculas de minúsculas.

## <a name="rule-description"></a>Descrição da regra

Os nomes de tipos criados pelo usuário não devem corresponder aos nomes dos namespaces referenciados que têm tipos visíveis externamente. A violação dessa regra pode reduzir a usabilidade da sua biblioteca.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Renomeie o tipo de modo que ele não corresponda ao nome de um namespace referenciado que tenha tipos visíveis externamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Para o novo desenvolvimento, nenhum cenário conhecido ocorre onde você deve suprimir um aviso dessa regra. Antes de suprimir o aviso, considere cuidadosamente como os usuários da biblioteca podem ser confundidos pelo nome correspondente. Para as bibliotecas de envio, talvez seja necessário suprimir um aviso dessa regra.