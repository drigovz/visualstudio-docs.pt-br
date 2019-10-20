---
title: 'CA2147: métodos transparentes não podem usar declarações de segurança | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610157"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: os métodos transparentes talvez não usem declarações de segurança
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O código marcado como <xref:System.Security.SecurityTransparentAttribute> não recebe permissões suficientes para Assert.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra analisa todos os métodos e tipos em um assembly que é de 100% transparente ou misto transparente/crítico e sinaliza qualquer uso declarativo ou imperativo de <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Em tempo de execução, todas as chamadas para <xref:System.Security.CodeAccessPermission.Assert%2A> do código Transparent farão com que uma <xref:System.InvalidOperationException> seja gerada. Isso pode ocorrer em assemblies de 100% Transparent e também em assemblies mistos/críticos, nos quais um método ou tipo é declarado transparente, mas inclui uma declaração declarativa ou imperativa.

 O [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 introduziu um recurso chamado *Transparency*. Os métodos, os campos, as interfaces, as classes e os tipos individuais podem ser transparentes ou críticos.

 O código transparent não tem permissão para elevar os privilégios de segurança. Portanto, todas as permissões concedidas ou exigidas por ele são passadas automaticamente pelo código para o domínio de aplicativo host ou chamador. Exemplos de elevações incluem declarações, LinkDemands, SuppressUnmanagedCode e código `unsafe`.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para resolver o problema, marque o código que chama a declaração com a <xref:System.Security.SecurityCriticalAttribute> ou remova a declaração.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir uma mensagem dessa regra.

## <a name="example"></a>Exemplo
 Esse código falhará se `SecurityTestClass` for transparente, quando o método `Assert` lançar um <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Exemplo
 Uma opção é codificar a revisão do método SecurityTransparentMethod no exemplo abaixo e, se o método for considerado seguro para elevação, Mark SecurityTransparentMethod com segurança crítica, isso exigirá uma segurança detalhada, completa e sem erros a auditoria deve ser executada no método junto com todos os limites que ocorrem dentro do método sob a declaração:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Outra opção é remover a declaração do código e permitir que qualquer permissão de e/s de arquivo subsequente flua para além do SecurityTransparentMethod para o chamador. Isso habilita as verificações de segurança. Nesse caso, nenhuma auditoria de segurança é geralmente necessária, pois as solicitações de permissão fluirão para o chamador e/ou o domínio do aplicativo. As demandas de permissão são fortemente controladas por meio da política de segurança, do ambiente de hospedagem e das concessões de permissão de código-fonte

## <a name="see-also"></a>Consulte também
 [Avisos de segurança](../code-quality/security-warnings.md)
