---
title: 'CA1903: Usar apenas a API da estrutura de destino'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 704972127130cc7be991213249ff41212fa40676
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233264"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Usar apenas a API da estrutura de destino

|||
|-|-|
|NomeDoTipo|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Categoria|Microsoft.Portability|
|Alteração significativa|Quebra-quando acionada na assinatura de um membro ou tipo visível externamente.<br /><br /> Não separável – quando disparado no corpo de um método.|

## <a name="cause"></a>Causa
Um membro ou tipo está usando um membro ou tipo que foi introduzido em um service pack que não foi incluído com a estrutura de destino do projeto.

## <a name="rule-description"></a>Descrição da regra
Novos membros e tipos foram incluídos no .NET Framework 2,0 Service Pack 1 e 2, .NET Framework 3,0 Service Pack 1 e 2 e .NET Framework 3,5 Service Pack 1. Os projetos que visam as versões principais do .NET Framework podem usar involuntariamente dependências dessas novas APIs. Para evitar essa dependência, essa regra é acionada em usos de novos membros e tipos que não foram incluídos por padrão com a estrutura de destino do projeto.

**Dependências de estrutura de destino e Service Pack**

|||
|-|-|
|Quando a estrutura de destino é|Acionado em usos de membros introduzidos em|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3,5|.NET Framework 3,5 SP1|
|.NET Framework 4|N/D|

Para alterar a estrutura de destino de um projeto [, consulte Como: Definir uma versão do .NET como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para remover a dependência no service pack, remova todos os usos do novo membro ou tipo. Se essa for uma dependência deliberada, suprima o aviso ou desative essa regra.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não omita um aviso dessa regra se essa não fosse uma dependência deliberada no service pack especificado. Nessa situação, seu aplicativo pode falhar ao ser executado em sistemas sem esse service pack instalado. Suprimir o aviso ou desativar essa regra se essa fosse uma dependência deliberada.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma classe que usa o tipo DateTimeOffset que está disponível somente no .NET 2,0 Service Pack 1. Este exemplo requer que .NET Framework 2,0 tenha sido selecionado na lista suspensa estrutura de destino nas propriedades do projeto.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Exemplo
O exemplo a seguir corrige a violação descrita anteriormente, substituindo os usos do tipo DateTimeOffset pelo tipo DateTime.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Consulte também

- [Avisos de portabilidade](../code-quality/portability-warnings.md)
- [Visão geral do direcionamento de estrutura](../ide/visual-studio-multi-targeting-overview.md)