---
title: 'CA1410: Métodos de registro COM devem ser correspondidos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a424e3c884d47b7deb848b418fbf0f3344d6c379
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714739"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Métodos de registro COM devem ser correspondidos

|||
|-|-|
|NomeDoTipo|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um tipo declara um método que é marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> de atributo, mas não declara um método que é marcado com o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo, ou vice-versa.

## <a name="rule-description"></a>Descrição da regra

Para clientes do modelo de objeto de componente (COM) criar um tipo .NET, o tipo deve ser registrado pela primeira vez. Se ele estiver disponível, um método que é marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributo é chamado durante o processo de registro para executar o código especificado pelo usuário. Um método correspondente que é marcado com o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributo é chamado durante o processo de cancelamento de registro para reverter as operações do método de registro.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicione o método de cancelamento de registro ou registro correspondente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo que viola a regra. O código comentado mostra a correção para a violação.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Regras relacionadas

[CA1411: OS métodos de registro não devem ser visíveis](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrar Assemblies com](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Ferramenta de Registro de Assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)