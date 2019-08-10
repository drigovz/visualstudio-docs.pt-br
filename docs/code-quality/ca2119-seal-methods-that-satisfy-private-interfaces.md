---
title: 'CA2119: Selar métodos que atendem a interfaces particulares'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 02e69a97468675cd6f7530793581c15717465d6f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921057"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Selar métodos que atendem a interfaces particulares

|||
|-|-|
|NomeDoTipo|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo público herdável fornece uma implementação de método substituível `internal` de`Friend` uma interface (no Visual Basic).

## <a name="rule-description"></a>Descrição da regra
Os métodos de interface têm acessibilidade pública, que não pode ser alterada pelo tipo de implementação. Uma interface interna cria um contrato que não deve ser implementado fora do assembly que define a interface. Um tipo público que implementa um método de uma interface interna usando o `virtual` modificador (`Overridable` in Visual Basic) permite que o método seja substituído por um tipo derivado que está fora do assembly. Se um segundo tipo no assembly de definição chamar o método e esperar um contrato somente interno, o comportamento poderá ser comprometido quando, em vez disso, o método substituído no assembly externo for executado. Isso cria uma vulnerabilidade de segurança.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, impeça que o método seja substituído fora do assembly usando um dos seguintes:

- Crie o tipo `sealed` declarativo (`NotInheritable` em Visual Basic).

- Altere a acessibilidade do tipo declarativo `internal` para`Friend` (em Visual Basic).

- Remova todos os construtores públicos do tipo declarativo.

- Implemente o método sem usar `virtual` o modificador.

- Implemente o método explicitamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se, após a revisão cuidadosa, não existir nenhum problema de segurança que possa ser explorável se o método for substituído fora do assembly.

## <a name="example-1"></a>Exemplo 1
O exemplo a seguir mostra um tipo `BaseImplementation`,, que viola essa regra.

[!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
[!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
[!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Exemplo 2
O exemplo a seguir explora a implementação do método virtual do exemplo anterior.

[!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
[!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
[!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Consulte também

- [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)
- [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)