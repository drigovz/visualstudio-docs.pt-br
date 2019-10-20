---
title: 'CA2205: usar equivalentes gerenciados da API do Win32 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 931b1e5099bf221fefc7a8f4a19524d2531a4418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609480"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: usar equivalentes gerenciados da API do Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um método de invocação de plataforma é definido e um método com a funcionalidade equivalente existe na biblioteca de classes [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="rule-description"></a>Descrição da Regra
 Um método de invocação de plataforma é usado para chamar uma função DLL não gerenciada e é definido usando o atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> ou a palavra-chave `Declare` em Visual Basic. Um método de invocação de plataforma definido incorretamente pode levar a exceções de tempo de execução devido a problemas como uma função de nome incorreta, mapeamento com falha de parâmetros e tipos de dados de valor de retorno, e especificações de campo incorretas, como a Convenção de chamada e o caractere Definição. Se disponível, geralmente é mais simples e menos propenso a erros chamar o método gerenciado equivalente do que definir e chamar o método não gerenciado diretamente. Chamar um método de plataforma Invoke também pode levar a problemas de segurança adicionais que precisam ser resolvidos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, substitua a chamada à função não gerenciada por uma chamada para seu equivalente gerenciado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso dessa regra se o método de substituição sugerido não fornecer a funcionalidade necessária.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma definição de método de invocação de plataforma que viola a regra. Além disso, as chamadas para o método de invocação de plataforma e o método gerenciado equivalente são mostradas.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1404: chamar GetLastError logo depois de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: mover P/Invokes para a classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: os pontos de entrada de P-Invoke devem existir](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: os P/Invokes não devem estar visíveis](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
