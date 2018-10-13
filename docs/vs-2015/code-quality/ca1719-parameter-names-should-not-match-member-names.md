---
title: 'CA1719: Os nomes de parâmetro não devem corresponder aos nomes de membros | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 13a6326391e543ef8220725ae982b8cfa75abb1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216667"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|NomeDoTipo|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um membro visível externamente corresponde, em uma comparação diferencia maiusculas de minúsculas, o nome de um dos seus parâmetros.

## <a name="rule-description"></a>Descrição da Regra
 Um nome de parâmetro deve informar o significado de um parâmetro e um nome de membro deve informar o significado de um membro. Seria um design raro se eles fossem iguais. A nomenclatura de um parâmetro com o mesmo nome do membro não é intuitiva e dificulta o uso da biblioteca.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Selecione um nome de parâmetro que não coincide com o nome do membro.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Para novos desenvolvimentos, nenhum conhecidos ocorrem de cenários em que você deve suprimir um aviso nessa regra. Para o envio de bibliotecas, talvez você precise suprimir um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)



