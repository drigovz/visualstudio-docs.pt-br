---
title: 'CA1408: não usar AutoDual ClassInterfaceType'
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
ms.openlocfilehash: 142d011ff73fbaf03af62164f962470f8feb3246
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440391"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: não usar AutoDual ClassInterfaceType

|||
|-|-|
|NomeDoTipo|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo visível Component Object Model (COM) é marcado com o atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> definido como o valor `AutoDual` de <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Descrição da regra
Tipos que usam uma interface dupla permitem que clientes sejam associados a um layout de interface específico. Todas as alterações feitas em uma versão futura do layout do tipo ou de qualquer tipo de base interromperão clientes COM associados à interface. Por padrão, se o atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> não for especificado, uma interface somente de expedição será usada.

A menos que marcado de outra forma, todos os tipos públicos não genéricos são visíveis para COM; todos os tipos não públicos e genéricos são invisíveis para COM.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o valor do atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> para o valor de `None` de <xref:System.Runtime.InteropServices.ClassInterfaceType> e defina explicitamente a interface.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir um aviso dessa regra, a menos que tenha certeza de que o layout do tipo e seus tipos base não serão alterados em uma versão futura.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma classe que viola a regra e uma redeclaração da classe para usar uma interface explícita.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1403: os tipos de layout automático não devem ser visíveis em COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412: marcar interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Consulte também

- [Qualificando tipos .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)
