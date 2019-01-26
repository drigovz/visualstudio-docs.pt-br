---
title: 'CA2004: Remover as chamadas a GC.KeepAlive'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2e2787b3d0876034113e777d7f8932d63e5c1a27
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001453"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Remover as chamadas a GC.KeepAlive

|||
|-|-|
|NomeDoTipo|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Classes usam `SafeHandle` , mas ainda contém chamadas para `GC.KeepAlive`.

## <a name="rule-description"></a>Descrição da regra
 Se você estiver convertendo em `SafeHandle` uso, remova todas as chamadas para `GC.KeepAlive` (objeto). Nesse caso, as classes não deve chamar `GC.KeepAlive`, supondo que eles não têm um finalizador, mas dependem `SafeHandle` para concluir o identificador de sistema operacional para eles.  Embora o custo de deixar em uma chamada para `GC.KeepAlive` pode ser insignificante, conforme medido pelo desempenho, a percepção de que uma chamada para `GC.KeepAlive` é necessária ou suficiente para resolver um problema que talvez não exista mais torna mais difícil para o código de tempo de vida Manter.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Remover chamadas para `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Você pode suprimir esse aviso somente se ele não é tecnicamente certo converter em `SafeHandle` uso na sua classe.