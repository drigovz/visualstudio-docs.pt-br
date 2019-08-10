---
title: 'CA1411: Métodos de registro COM não devem ser visíveis'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f6f40308255e0496b2bcccddf4299e83ea93100
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922045"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Métodos de registro COM não devem ser visíveis

|||
|-|-|
|NomeDoTipo|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um método que é marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo é visível externamente.

## <a name="rule-description"></a>Descrição da regra
Quando um assembly é registrado com Component Object Model (COM), as entradas são adicionadas ao registro para cada tipo visível COM no assembly. Os métodos que são marcados com <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> os <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributos e são chamados durante os processos de registro e cancelamento de registro, respectivamente, para executar o código de usuário específico para o registro/cancelamento de registro desses tipos. Esse código não deve ser chamado fora desses processos.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere a acessibilidade do método `private` para ou `internal` (`Friend` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra dois métodos que violam a regra.

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1410: Os métodos de registro COM devem ser correspondidos](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrando assemblies usando COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Ferramenta de Registro de Assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)