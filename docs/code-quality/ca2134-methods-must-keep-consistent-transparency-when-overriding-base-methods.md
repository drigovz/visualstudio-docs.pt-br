---
title: 'CA2134: Os métodos devem manter uma transparência consistente durante a substituição dos métodos base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 517588826983613c71a74296914b1dfeb3eaa2b4
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253309"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Os métodos devem manter uma transparência consistente durante a substituição dos métodos base

|||
|-|-|
|NomeDoTipo|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Essa regra é acionada quando um método marcado <xref:System.Security.SecurityCriticalAttribute> com o substitui um método que é transparente ou marcado <xref:System.Security.SecuritySafeCriticalAttribute>com. A regra também é acionada quando um método que é transparente ou marcado <xref:System.Security.SecuritySafeCriticalAttribute> com o substitui um método que é marcado <xref:System.Security.SecurityCriticalAttribute>com um.

A regra é aplicada durante a substituição de um método virtual ou a implementação de uma interface.

## <a name="rule-description"></a>Descrição da regra
Essa regra é acionada em tentativas de alterar a acessibilidade de segurança de um método além da cadeia de herança. Por exemplo, se um método virtual em uma classe base for transparente ou de segurança crítica, a classe derivada deverá substituí-la por um método transparente ou de segurança crítica. Por outro lado, se a segurança da máquina virtual for crítica, a classe derivada deverá substituí-la por um método crítico de segurança. A mesma regra se aplica à implementação de métodos de interface.

As regras de transparência são impostas quando o código é compilado JIT em vez de em tempo de execução, para que o cálculo de transparência não tenha informações de tipo dinâmico. Portanto, o resultado do cálculo de transparência deve ser capaz de ser determinado exclusivamente dos tipos estáticos que estão sendo compilados em JIT, independentemente do tipo dinâmico.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere a transparência do método que está substituindo um método virtual ou implementando uma interface para corresponder à transparência do método virtual ou da interface.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir avisos desta regra. As violações dessa regra resultam em um tempo <xref:System.TypeLoadException> de execução para assemblies que usam transparência de nível 2.

## <a name="examples"></a>Exemplos

### <a name="code"></a>Código
[!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>Consulte também
[Segurança-código Transparent, nível 2](/dotnet/framework/misc/security-transparent-code-level-2)