---
title: 'CA1409: Tipos visíveis no COM devem poder ser criados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4196cb91e1b866453de54347b8a67edd3dc2dc96
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921891"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Tipos visíveis no COM devem poder ser criados

|||
|-|-|
|NomeDoTipo|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo de referência que é marcado especificamente como visível para Component Object Model (COM) contém um construtor público com parâmetros, mas não contém um construtor público padrão (sem parâmetros).

## <a name="rule-description"></a>Descrição da regra
Um tipo sem um construtor padrão público não pode ser criado por clientes COM. No entanto, o tipo ainda pode ser acessado por clientes COM, se outro meio estiver disponível para criar o tipo e passá-lo para o cliente (por exemplo, por meio do valor de retorno de uma chamada de método).

A regra ignora os tipos derivados de <xref:System.Delegate?displayProperty=fullName>.

Por padrão, os itens a seguir são visíveis para COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, adicione um construtor público padrão ou remova o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> do tipo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se outras maneiras forem fornecidas para criar e passar o objeto para o cliente COM.

## <a name="related-rules"></a>Regras relacionadas
[CA1017: Marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também

- [Qualificando tipos .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)