---
title: 'CA2004: remover chamadas para GC. KeepAlive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e34a8e7d4860a599155554410e13df5a6eb3bfe1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672492"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: remover chamadas para GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Categoria|Microsoft. confiabilidade|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 As classes usam `SafeHandle`, mas ainda contêm chamadas para `GC.KeepAlive`.

## <a name="rule-description"></a>Descrição da Regra
 Se você estiver convertendo para uso `SafeHandle`, remova todas as chamadas para `GC.KeepAlive` (objeto). Nesse caso, as classes não devem chamar `GC.KeepAlive`, supondo que não tenham um finalizador, mas que dependem de `SafeHandle` para concluir o identificador do sistema operacional para eles.  Embora o custo de deixar em uma chamada para `GC.KeepAlive` possa ser insignificante como medido pelo desempenho, a percepção de que uma chamada para `GC.KeepAlive` é necessária ou suficiente para resolver um problema de tempo de vida que pode não existir mais para que o código seja mais difícil de manter.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova as chamadas para `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você pode suprimir esse aviso somente se não estiver tecnicamente correto para converter em uso `SafeHandle` em sua classe.
