---
title: 'CA1033: Métodos de interface devem ser chamados por tipos filho'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10db644fe4cf65a7336ef8bd50dcf62e072e1c46
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922962"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Métodos de interface devem ser chamados por tipos filho

|||
|-|-|
|NomeDoTipo|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Categoria|Microsoft.Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo visível externamente sem lacre fornece uma implementação de método explícita de uma interface pública e não fornece um método visível externamente alternativo com o mesmo nome.

## <a name="rule-description"></a>Descrição da regra
Considere um tipo base que implementa explicitamente um método de interface pública. Um tipo que deriva do tipo base pode acessar o método de interface herdado somente por meio de uma referência à instância atual`this` ( C#em) que é convertida para a interface. Se o tipo derivado reimplementar (explicitamente) o método de interface herdado, a implementação base não poderá mais ser acessada. A chamada por meio da referência de instância atual invocará a implementação derivada; Isso causa recursão e um estouro de pilha eventual.

Essa regra não relata uma violação para uma implementação explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando um método ou `System.IDisposable.Dispose(Boolean)` visível `Close()` externamente é fornecido.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente um novo método que expõe a mesma funcionalidade e que seja visível para tipos derivados ou altere para uma implementação não explícita. Se uma alteração significativa for aceitável, uma alternativa é tornar o tipo lacrado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se for fornecido um método externo visível que tenha a mesma funcionalidade, mas um nome diferente do método implementado explicitamente.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo `ViolatingBase`,, que viola a regra e um tipo, `FixedBase`, que mostra uma correção para a violação.

[!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Consulte também
[Interfaces](/dotnet/csharp/programming-guide/interfaces/index)