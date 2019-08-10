---
title: 'CA2004: Remover as chamadas a GC.KeepAlive'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a716da8eb0fb1b741c302ed32408e63a4933567b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921134"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Remover as chamadas a GC.KeepAlive

|||
|-|-|
|NomeDoTipo|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
As classes `SafeHandle` usam, mas ainda contêm `GC.KeepAlive`chamadas para.

## <a name="rule-description"></a>Descrição da regra
Se você estiver convertendo `SafeHandle` para uso, remova todas as `GC.KeepAlive` chamadas para (Object). Nesse caso, as classes não devem chamar `GC.KeepAlive`, supondo que elas não tenham um finalizador, mas que `SafeHandle` dependam do para concluir o identificador do sistema operacional para elas.  Embora o custo de deixar em uma chamada para `GC.KeepAlive` pode ser insignificante como medido pelo desempenho, a percepção de `GC.KeepAlive` que uma chamada é necessária ou suficiente para resolver um problema de tempo de vida que pode não existir mais torna o código mais difícil conservar.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Remova as chamadas `GC.KeepAlive`para.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Você pode suprimir esse aviso somente se não estiver tecnicamente correto para converter para `SafeHandle` uso em sua classe.