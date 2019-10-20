---
title: 'CA1804: remover locais não utilizados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 824a65e765f21748b97292beea64ea6c9bd64a1b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671557"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: remover locais não usados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|RemoveUnusedLocals|
|CheckId|CA1804|
|Categoria|Microsoft. performance|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um método declara uma variável local, mas não usa a variável, exceto possivelmente como o destinatário de uma instrução de atribuição. Para análise por essa regra, o assembly testado deve ser criado com informações de depuração e o arquivo de banco de dados do programa (. pdb) associado deve estar disponível.

## <a name="rule-description"></a>Descrição da Regra
 As variáveis locais não utilizadas e as atribuições desnecessárias aumentam o tamanho de um assembly e diminuem o desempenho.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova ou use a variável local. Observe que o C# compilador incluído com [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] remove variáveis locais não utilizadas quando a opção `optimize` está habilitada.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso dessa regra se a variável foi emitida pelo compilador. Também é seguro suprimir um aviso dessa regra ou desabilitar a regra, se o desempenho e a manutenção de código não forem preocupações principais.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra várias variáveis locais não utilizadas.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1809: evitar locais excessivos](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: examinar parâmetros não usados](../code-quality/ca1801-review-unused-parameters.md)
