---
title: 'CA2214: não chamar métodos substituíveis em construtores | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662905"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: não chamar métodos substituíveis em construtores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 O construtor de um tipo sem lacre chama um método virtual definido em sua classe.

## <a name="rule-description"></a>Descrição da Regra
 Quando um método virtual é chamado, o tipo real que executa o método não é selecionado até o tempo de execução. Quando um construtor chama um método virtual, é possível que o construtor da instância que invoca o método não tenha sido executado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, não chame os métodos virtuais de um tipo de dentro dos construtores do tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. O construtor deve ser reprojetado para eliminar a chamada para o método virtual.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o efeito de violar essa regra. O aplicativo de teste cria uma instância de `DerivedType`, que faz com que seu construtor de classe base (`BadlyConstructedType`) seja executado. o construtor de `BadlyConstructedType` chama incorretamente o método virtual `DoSomething`. Como mostra a saída, `DerivedType.DoSomething()` é executado e faz isso antes que o construtor de `DerivedType` seja executado.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Este exemplo gerencia a seguinte saída.

 **Chamando o construtor base.** 
**algo derivado é chamado-Initialized? Nenhum** 
**chamando o Construtor derivado.**
