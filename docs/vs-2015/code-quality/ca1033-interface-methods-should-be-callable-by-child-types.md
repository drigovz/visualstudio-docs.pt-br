---
title: 'CA1033: Métodos de interface devem ser chamáveis por tipos filho | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bd801e7afc1fa0a4edf043aba560bc4afcdae9de
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682839"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Métodos de interface devem ser chamados por tipos filho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um tipo visível externamente sem lacre fornece uma implementação de método explícita de uma interface pública e não fornece um método visível externamente alternativo com o mesmo nome.

## <a name="rule-description"></a>Descrição da Regra
 Considere um tipo base que implementa explicitamente um método de interface pública. Um tipo derivado do tipo base pode acessar o método de interface herdada apenas por meio de uma referência à instância atual (`this` em c#) que é convertido para a interface. Se o tipo derivado novamente (explicitamente) implementa o método de interface herdada, a implementação base não pode mais ser acessada. A chamada por meio de referência de instância atual invocará a implementação derivada; Isso causa recursão e um estouro de pilha eventual.

 Essa regra não relata uma violação para uma implementação explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando um visível externamente `Close()` ou `System.IDisposable.Dispose(Boolean)` método é fornecido.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, implemente um novo método que expõe a mesma funcionalidade e é visível para tipos derivados ou alterar para uma implementação não explícitas. Se uma alteração significativa é aceitável, uma alternativa é tornar o tipo selado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se um método visível externamente é fornecida que tem a mesma funcionalidade, mas o método implementado explicitamente um nome diferente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `ViolatingBase`, que viola a regra e um tipo, `FixedBase`, que mostra uma correção para a violação.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Consulte também
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
