---
title: 'CA1031: Não capturar tipos de exceção geral'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236062"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Não capturar tipos de exceção geral

|||
|-|-|
|NomeDoTipo|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Uma exceção <xref:System.Exception?displayProperty=fullName> geral, como ou <xref:System.SystemException?displayProperty=fullName> é capturada em `catch` uma instrução `catch()` , ou uma cláusula catch geral, como é usada.

## <a name="rule-description"></a>Descrição da regra
As exceções gerais não devem ser capturadas.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, Capture uma exceção mais específica ou relance a exceção geral como a última instrução no `catch` bloco.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra. A captura de tipos de exceção gerais pode ocultar os problemas de tempo de execução do usuário da biblioteca e tornar a depuração mais difícil.

> [!NOTE]
> A partir do .NET Framework 4, o Common Language Runtime (CLR) não entrega mais exceções de estado corrompido que ocorrem no sistema operacional e no código gerenciado, como violações de [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]acesso no, a serem manipuladas pelo código gerenciado. Se você quiser compilar um aplicativo no .NET Framework 4 ou em versões posteriores e manter o tratamento de exceções de estado corrompidas, poderá <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> aplicar o atributo ao método que manipula a exceção de estado corrompido.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola essa regra e um tipo que implementa corretamente o `catch` bloco.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2200: Relançar para preservar os detalhes da pilha](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)