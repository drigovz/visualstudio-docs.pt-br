---
title: 'CA1822: Marcar membros como estáticos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ebbbbe01f1dd23dfc560e019133dacd3517b388
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253459"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Marcar membros como estáticos

|||
|-|-|
|NomeDoTipo|MarkMembersAsStatic|
|CheckId|CA1822|
|Categoria|Microsoft.Performance|
|Alteração significativa|Não separável – se o membro não estiver visível fora do assembly, independentemente da alteração feita. Não separável – se você simplesmente alterar o membro para um membro de instância com a `this` palavra-chave.<br /><br /> Quebrando – se você alterar o membro de um membro de instância para um membro estático e ele estiver visível fora do assembly.|

## <a name="cause"></a>Causa
Um membro que não acessa dados de instância não está marcado como estático (compartilhado em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Descrição da regra
Os membros que não acessam dados da instância ou os métodos da instância de chamada podem ser marcados como estáticos (Shared no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Depois que você marcar os métodos como estáticos, o compilador emitirá sites de chamada não virtuais para esses membros. A emissão de sites de chamadas não virtuais impedirá uma verificação no tempo de execução para cada chamada, o que garante que o ponteiro do objeto atual seja não nulo. Isso pode obter um alto desempenho mensurável para o código sensível ao desempenho. Em alguns casos, a falha ao acessar a instância do objeto atual representa um problema de correção.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Marque o membro como estático (ou compartilhado [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ou use ' this '/' me ' no corpo do método, se apropriado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra para o código fornecido anteriormente para o qual a correção seria uma alteração significativa.

## <a name="related-rules"></a>Regras relacionadas
[CA1811: Evitar código particular não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Evitar classes internas não instanciadas](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)