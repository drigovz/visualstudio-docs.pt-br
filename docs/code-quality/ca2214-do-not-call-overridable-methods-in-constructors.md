---
title: 'CA2214: Não chamar métodos substituíveis em construtores'
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8eb881da0a7ed243bda35079f617a314053f2d85
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231299"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Não chamar métodos substituíveis em construtores

|||
|-|-|
|NomeDoTipo|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

O construtor de um tipo sem lacre chama um método virtual definido em sua classe.

## <a name="rule-description"></a>Descrição da regra

Quando um método virtual é chamado, o tipo real que executa o método não é selecionado até o tempo de execução. Quando um construtor chama um método virtual, é possível que o construtor da instância que invoca o método não tenha sido executado.

> [!NOTE]
> A implementação de análise herdada dessa regra tem uma mensagem de diagnóstico diferente**de "\[nome do Construtor] contém uma cadeia de chamada que resulta em uma chamada para um método virtual definido pela classe. Examine a seguinte pilha de chamadas para consequências**indesejadas ". A implementação de [analisadores do FxCop](install-fxcop-analyzers.md) dessa regra tem uma mensagem de diagnóstico "**não chamar métodos substituíveis em construtores**".

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, não chame os métodos virtuais de um tipo de dentro dos construtores do tipo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. O construtor deve ser reprojetado para eliminar a chamada para o método virtual.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra o efeito de violar essa regra. O aplicativo de teste cria uma instância `DerivedType`do, que faz com que seu`BadlyConstructedType`Construtor de classe base () seja executado. `BadlyConstructedType`o construtor do chama incorretamente o método `DoSomething`virtual. Como mostra a saída, `DerivedType.DoSomething()` o é executado `DerivedType`antes de executar o construtor.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Este exemplo gera a seguinte saída:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```