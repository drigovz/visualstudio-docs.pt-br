---
title: 'CA1412: marcar interfaces de origem como IDispatch | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652725"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: marcar interfaces ComSource como IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo é marcado com o atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> e pelo menos uma interface especificada não é marcada com o atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> definido como o valor `InterfaceIsDispatch`.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> é usado para identificar as interfaces de evento que uma classe expõe para clientes Component Object Model (COM). Essas interfaces devem ser expostas como `InterfaceIsIDispatch` para permitir que Visual Basic COM clientes COM 6 recebam notificações de eventos. Por padrão, se uma interface não estiver marcada com o atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, ela será exposta como uma interface dupla.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione ou modifique o atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> para que seu valor seja definido como InterfaceIsIDispatch para todas as interfaces especificadas com o atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma classe em que uma das interfaces viola a regra.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Consulte também
 [Como gerar eventos manipulados por um coletor de com](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [interoperação com código não gerenciado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
