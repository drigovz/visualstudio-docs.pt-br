---
title: 'CA1408: Não usar AutoDual ClassInterfaceType'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b79483e8703ea297634d0d81d5449c09b58c9fb7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921977"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Não usar AutoDual ClassInterfaceType

|||
|-|-|
|NomeDoTipo|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo de Component Object Model (com) visível é marcado com <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> o atributo definido como `AutoDual` o valor <xref:System.Runtime.InteropServices.ClassInterfaceType>de.

## <a name="rule-description"></a>Descrição da regra
Tipos que usam uma interface dupla permitem que clientes sejam associados a um layout de interface específico. Todas as alterações feitas em uma versão futura do layout do tipo ou de qualquer tipo de base interromperão clientes COM associados à interface. Por padrão, se o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo não for especificado, uma interface somente de expedição será usada.

A menos que marcado de outra forma, todos os tipos públicos não genéricos são visíveis para COM; todos os tipos não públicos e genéricos são invisíveis para COM.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o valor do <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo para o `None` valor de <xref:System.Runtime.InteropServices.ClassInterfaceType> e defina explicitamente a interface.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir um aviso dessa regra, a menos que tenha certeza de que o layout do tipo e seus tipos base não serão alterados em uma versão futura.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma classe que viola a regra e uma redeclaração da classe para usar uma interface explícita.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1403: Os tipos de layout automático não devem ser visíveis no COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412: Marcar interfaces de origem como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Consulte também

- [Qualificando tipos .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)