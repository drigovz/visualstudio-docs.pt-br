---
title: 'CA1410: os métodos de registro COM devem ser correspondidos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30f507f07de858dc222b4824ac6da633c76812ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652740"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: os métodos de registro COM devem ser correspondentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo declara um método que é marcado com o atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, mas não declara um método que é marcado com o atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, ou vice-versa.

## <a name="rule-description"></a>Descrição da Regra
 Para clientes de Component Object Model (COM) criarem um tipo de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], o tipo deve primeiro ser registrado. Se estiver disponível, um método marcado com o atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> será chamado durante o processo de registro para executar o código especificado pelo usuário. Um método correspondente que é marcado com o atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> é chamado durante o processo de cancelamento de registro para inverter as operações do método de registro.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione o registro ou o método de cancelamento de registro correspondente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra. O código comentado mostra a correção para a violação.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1411: os métodos de registro COM não devem estar visíveis](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [registrar assemblies com o](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [REGASM. exe com (ferramenta de registro de assembly)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
