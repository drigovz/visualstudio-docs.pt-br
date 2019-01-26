---
title: 'CA2122: Não expor indiretamente métodos com demandas de link'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 701b44b8018e7493305c5269a38908c454889b9c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986144"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Não expor indiretamente métodos com demandas de link

|||
|-|-|
|NomeDoTipo|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um membro público ou protegido tem um [demandas de Link](/dotnet/framework/misc/link-demands) e é chamado por um membro que não executa nenhuma verificação de segurança.

## <a name="rule-description"></a>Descrição da regra
 Uma exigência de vínculo verifica as permissões apenas do chamador imediato. Se um membro `X` não faz com que nenhum demandas de segurança de seus chamadores e chamadas de código protegido por uma demanda de link em um chamador sem a permissão necessária pode usar `X` para acessar o membro protegido.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Adicionar uma segurança [dados e modelagem](/dotnet/framework/data/index) ou vincular a demanda para o membro para que ele não fornece mais acesso desprotegido para o membro protegido por demanda de link.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Para suprimir com segurança um aviso nessa regra, certifique-se de que seu código não concede seus chamadores acesso a recursos que podem ser usados de forma destrutivas ou operações.

## <a name="example-1"></a>Exemplo 1
 Os exemplos a seguir mostram uma biblioteca que viola a regra e um aplicativo que demonstra a desvantagem da biblioteca. A biblioteca de exemplo fornece dois métodos que juntos violam a regra. O `EnvironmentSetting` método é protegido por uma demanda de link para acesso irrestrito a variáveis de ambiente. O `DomainInformation` método não faz nenhuma demandas de segurança de seus chamadores antes de chamar `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Exemplo 2
 O aplicativo a seguir chama o membro da biblioteca não segura.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Este exemplo gera a seguinte saída:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)
- [Demandas de link](/dotnet/framework/misc/link-demands)
- [Dados e modelagem](/dotnet/framework/data/index)