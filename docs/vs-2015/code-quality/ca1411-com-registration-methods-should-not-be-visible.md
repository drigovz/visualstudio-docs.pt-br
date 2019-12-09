---
title: 'CA1411: os métodos de registro COM não devem ser visíveis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ddd2c90d23884bd08a90560dcc5ed0fe700aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652720"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: os métodos de registro COM não devem estar visíveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método que é marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou o atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> é visível externamente.

## <a name="rule-description"></a>Descrição da Regra
 Quando um assembly é registrado com Component Object Model (COM), as entradas são adicionadas ao registro para cada tipo visível COM no assembly. Os métodos que são marcados com os atributos <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> e <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> são chamados durante os processos de registro e cancelamento de registro, respectivamente, para executar o código de usuário específico ao registro/cancelamento de registro desses tipos. Esse código não deve ser chamado fora desses processos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere a acessibilidade do método para `private` ou `internal` (`Friend` em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois métodos que violam a regra.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1410: os métodos de registro COM devem ser correspondentes](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [registrar assemblies com o](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [REGASM. exe com (ferramenta de registro de assembly)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
