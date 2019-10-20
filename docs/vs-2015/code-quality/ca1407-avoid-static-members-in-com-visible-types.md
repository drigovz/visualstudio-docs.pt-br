---
title: 'CA1407: evitar membros estáticos em tipos visíveis do COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6996d210417a56dd83532c481aaa0dc80b9f23ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655242"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: evitar membros estáticos em tipos visíveis COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo marcado especificamente como visível para Component Object Model (COM) contém um método `public``static`.

## <a name="rule-description"></a>Descrição da Regra
 COM não oferece suporte a métodos `static`.

 Essa regra ignora os acessadores de propriedade e evento, métodos de sobrecarga de operador ou métodos que são marcados usando o atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou o atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

 Por padrão, os itens a seguir são visíveis para COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público.

 Para que essa regra ocorra, um nível de assembly <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve ser definido como `false` e a classe-<xref:System.Runtime.InteropServices.ComVisibleAttribute> deve ser definida como `true`, como mostra o código a seguir.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o design para usar um método de instância que forneça a mesma funcionalidade que o método `static`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se um cliente COM não precisar de acesso à funcionalidade fornecida pelo método `static`.

## <a name="example-violation"></a>Violação de exemplo

### <a name="description"></a>Descrição
 O exemplo a seguir mostra um método `static` que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Comentários
 Neste exemplo, o método **book. FromPages** não pode ser chamado de com.

## <a name="example-fix"></a>Correção de exemplo

### <a name="description"></a>Descrição
 Para corrigir a violação no exemplo anterior, você pode alterar o método para um método de instância, mas isso não faz sentido nessa instância. Uma solução melhor é aplicar explicitamente `ComVisible(false)` ao método para deixá-lo claro para outros desenvolvedores que o método não pode ser visto do COM.

 O exemplo a seguir aplica <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> ao método.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: evitar argumentos Int64 para clientes do Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: evitar campos não públicos em tipos de valor visíveis em COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Consulte também
 [Interoperação com código não gerenciado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
