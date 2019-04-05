---
title: 'CA2214: Não chamar métodos substituíveis em construtores | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a2e107429bb48b2bf17a625e25866a19c7781b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923440"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Não chamar métodos substituíveis em construtores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 O construtor de um tipo sem lacre chama um método virtual definido na sua classe.

## <a name="rule-description"></a>Descrição da Regra
 Quando um método virtual é chamado, o tipo real que executa o método não está selecionado até o tempo de execução. Quando um construtor chama um método virtual, é possível que o construtor para a instância que invoca o método não executado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, não chame métodos virtuais de um tipo de dentro de construtores do tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. O construtor deve ser reformulado para eliminar a chamada para o método virtual.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o efeito de violação dessa regra. O aplicativo de teste cria uma instância de `DerivedType`, que faz com que sua classe base (`BadlyConstructedType`) construtor ser executado. `BadlyConstructedType`do construtor incorretamente chama o método virtual `DoSomething`. Como mostra a saída, `DerivedType.DoSomething()` executa e faz, portanto, antes de `DerivedType`do construtor é executado.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Este exemplo gerencia a seguinte saída.

 **Chamando o construtor base. ** 
 **DoSomething derivado é chamado - inicializado? Não**
**chamada derivado ctor.**
