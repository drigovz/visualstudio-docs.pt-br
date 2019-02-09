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
ms.openlocfilehash: f81327324de937df57edfb36cae34d613f6298a5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953965"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Nomes de tipo não devem corresponder a namespaces

|||
|-|-|
|NomeDoTipo|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um nome de tipo corresponde a um nome de namespace referenciado que tenha um ou mais tipos visíveis externamente. A comparação de nome não diferencia maiusculas de minúsculas.

## <a name="rule-description"></a>Descrição da regra

Nomes de tipo criados pelo usuário não devem corresponder a nomes de namespaces referenciados que têm tipos visíveis externamente. A violação dessa regra pode reduzir a usabilidade da biblioteca.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Renomear o tipo, de modo que ele não corresponder ao nome de um namespace referenciado que tenha tipos visíveis externamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Para novos desenvolvimentos, nenhum conhecidos ocorrem de cenários em que você deve suprimir um aviso nessa regra. Antes de você suprime o aviso, considere cuidadosamente como os usuários da sua biblioteca talvez estejam confusos pelas nome correspondente. Para o envio de bibliotecas, talvez você precise suprimir um aviso nessa regra.