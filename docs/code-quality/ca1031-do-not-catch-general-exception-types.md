---
title: 'CA1031: não capturar tipos de exceção gerais'
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
ms.openlocfilehash: e157feb9b054cd6082f77c4f86277c35ddb02c34
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349128"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: não capturar tipos de exceção gerais

|||
|-|-|
|NomeDoTipo|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Categoria|Microsoft. Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Uma exceção geral, como <xref:System.Exception?displayProperty=fullName> ou <xref:System.SystemException?displayProperty=fullName>, é capturada em uma instrução `catch` ou uma cláusula catch geral, como `catch()`, é usada.

## <a name="rule-description"></a>Descrição da regra
As exceções gerais não devem ser capturadas.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, Capture uma exceção mais específica ou relance a exceção geral como a última instrução no bloco `catch`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra. A captura de tipos de exceção gerais pode ocultar os problemas de tempo de execução do usuário da biblioteca e tornar a depuração mais difícil.

> [!NOTE]
> A partir do .NET Framework 4, o Common Language Runtime (CLR) não entrega mais exceções de estado corrompidas que ocorrem no sistema operacional e no código gerenciado, como violações de acesso no [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], a serem manipuladas pelo código gerenciado. Se você quiser compilar um aplicativo no .NET Framework 4 ou em versões posteriores e manter o tratamento de exceções de estado corrompidas, poderá aplicar o atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> ao método que manipula a exceção de estado corrompido.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola essa regra e um tipo que implementa corretamente o bloco `catch`.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2200: relançar para preservar detalhes da pilha](../code-quality/ca2200.md)