---
title: 'CA2117: Os tipos APTCA só devem estender os tipos base APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09fa055fbf1b11e06b1dde32df5a316a3ec39848
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658651"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Tipos APTCA devem estender somente tipos base APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido em um assembly com o atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> é herdado de um tipo declarado em um assembly que não tem o atributo.

## <a name="rule-description"></a>Descrição da Regra
 Por padrão, os tipos públicos ou protegidos em assemblies com nomes fortes são implicitamente protegidos por uma [exigência de herança](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) para confiança total. Os assemblies com nome forte marcados com o atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) não têm essa proteção. O atributo desabilita a demanda de herança. Isso torna os tipos expostos declarados no assembly herdáveis por tipos que não têm confiança total.

 Quando o atributo APTCA está presente em um assembly totalmente confiável e um tipo no assembly é herdado de um tipo que não permite chamadores parcialmente confiáveis, uma exploração de segurança é possível. Se dois tipos `T1` e `T2` atenderem às seguintes condições, os chamadores mal-intencionados poderão usar o tipo `T1` para ignorar a demanda de herança de confiança total implícita que protege o `T2`:

- `T1` é um tipo público declarado em um assembly totalmente confiável que tem o atributo APTCA.

- `T1` é herdado de um tipo `T2` fora de seu assembly.

- o assembly de `T2` não tem o atributo APTCA e, portanto, não deve ser herdável por tipos em assemblies parcialmente confiáveis.

  Um tipo parcialmente confiável `X` pode herdar de `T1`, o que fornece acesso a membros herdados declarados em `T2`. Como `T2` não tem o atributo APTCA, seu tipo derivado imediato (`T1`) deve atender a uma demanda de herança para confiança total; o `T1` tem confiança total e, portanto, satisfaz essa verificação. O risco de segurança é porque `X` não participa da demanda de herança que protege `T2` contra subclasses não confiáveis. Por esse motivo, os tipos com o atributo APTCA não devem estender tipos que não tenham o atributo.

  Outro problema de segurança, e talvez um mais comum, é que o tipo derivado (`T1`) pode, através de um erro de programador, expor membros protegidos do tipo que requer confiança total (`T2`). Quando isso ocorre, chamadores não confiáveis têm acesso a informações que devem estar disponíveis somente para tipos totalmente confiáveis.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Se o tipo relatado pela violação estiver em um assembly que não requer o atributo APTCA, remova-o.

 Se o atributo APTCA for necessário, adicione uma solicitação de herança para confiança total ao tipo. Isso protege contra herança por tipos não confiáveis.

 É possível corrigir uma violação adicionando o atributo APTCA aos assemblies dos tipos base relatados pela violação. Não faça isso sem primeiro realizar uma revisão de segurança intensiva de todo o código nos assemblies e de todo o código que depende dos assemblies.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Para suprimir um aviso dessa regra com segurança, você deve garantir que os membros protegidos expostos pelo seu tipo não façam direta ou indiretamente que os chamadores não confiáveis acessem informações confidenciais, operações ou recursos que podem ser usados de maneira destrutiva.

## <a name="example"></a>{1&gt;Exemplo&lt;1}
 O exemplo a seguir usa dois assemblies e um aplicativo de teste para ilustrar a vulnerabilidade de segurança detectada por essa regra. O primeiro assembly não tem o atributo APTCA e não deve ser herdável por tipos parcialmente confiáveis (representados por `T2` na discussão anterior).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>{1&gt;Exemplo&lt;1}
 O segundo assembly, representado pelo `T1` na discussão anterior, é totalmente confiável e permite chamadores parcialmente confiáveis.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>{1&gt;Exemplo&lt;1}
 O tipo de teste, representado por `X` na discussão anterior, está em um assembly parcialmente confiável.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **Conheça o sombreador glen 2/22/2003 12:00:00 am!** 
**do teste: o ensolarado campina** 
 se**reunir no ensolarado Campina 2/22/2003 12:00:00 am!**
## <a name="related-rules"></a>Regras relacionadas
 [CA2116: Os métodos APTCA só devem chamar os métodos APTCA ](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Consulte também
 [Diretrizes de codificação seguras](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework assemblies que podem ser chamados por código parcialmente confiável](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [usando bibliotecas de [demandas de herança](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) de código parcialmente confiáveis](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74)
