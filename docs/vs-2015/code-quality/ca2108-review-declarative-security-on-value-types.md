---
title: 'CA2108: Revisar segurança declarativa em tipos de valor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f6a17bf57f00923cfd31bd477f211ba66169672a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687364"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Examinar a segurança declarativa em tipos de valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo de valor público ou protegido é protegido por um [dados e modelagem](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) ou [demandas de Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descrição da Regra
 Tipos de valor são alocados e inicializados por seus construtores padrão antes de executar outros construtores. Se um tipo de valor é protegido por um Demand ou LinkDemand e o chamador não tem permissões que satisfazem a verificação de segurança, qualquer construtor diferente do padrão falhará e será gerada uma exceção de segurança. O tipo de valor não é desalocado; ele é deixado no estado definido pelo seu construtor padrão. Não presuma que um chamador que passa uma instância do tipo de valor tem permissão para criar ou acessar a instância.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Você não pode corrigir uma violação dessa regra, a menos que você remover a verificação de segurança do tipo e verificações de segurança de nível de método de uso em seu lugar. Observe que corrigir a violação dessa maneira não impedirá que os chamadores com permissões inadequadas obtenham as instâncias do tipo de valor. Você deve garantir que uma instância do tipo de valor, em seu estado padrão, não expõe informações confidenciais e não pode ser usada de modo prejudicial.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você pode suprimir um aviso nessa regra, se qualquer chamador pode obter as instâncias do tipo do valor em seu estado padrão sem apresentando uma ameaça à segurança.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma biblioteca que contém um tipo de valor que viola essa regra. Observe que o `StructureManager` tipo pressupõe que um chamador que passa uma instância do tipo de valor tem permissão para criar ou acessar a instância.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir demonstra a desvantagem da biblioteca.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **Construtor personalizado da estrutura: Falha na solicitação.** 
**Novos valores SecuredTypeStructure 100 100**
**SecuredTypeStructure 200 200 de novos valores**
## <a name="see-also"></a>Consulte também
 [Demandas de link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dados e modelagem](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
