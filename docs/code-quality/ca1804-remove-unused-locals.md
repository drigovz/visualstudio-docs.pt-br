---
title: 'CA1804: Remover locais não utilizados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0a83d0afffc50c7697fad98c4dc49e31770d63d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233748"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Remover locais não utilizados

|||
|-|-|
|NomeDoTipo|RemoveUnusedLocals|
|CheckId|CA1804|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um método declara uma variável local, mas não usa a variável, exceto possivelmente como o destinatário de uma instrução de atribuição. Para análise por essa regra, o assembly testado deve ser criado com informações de depuração e o arquivo de banco de dados do programa (. pdb) associado deve estar disponível.

## <a name="rule-description"></a>Descrição da regra
As variáveis locais não utilizadas e as atribuições desnecessárias aumentam o tamanho de um assembly e diminuem o desempenho.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova ou use a variável local.

> [!NOTE]
> O C# compilador remove as variáveis locais não usadas quando `optimize` a opção está habilitada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir um aviso dessa regra se a variável foi emitida pelo compilador. Também é seguro suprimir um aviso dessa regra ou desabilitar a regra, se o desempenho e a manutenção de código não forem preocupações principais.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra várias variáveis locais não utilizadas.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1809: Evitar locais em excesso](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: Evitar código particular não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Evitar classes internas não instanciadas](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)