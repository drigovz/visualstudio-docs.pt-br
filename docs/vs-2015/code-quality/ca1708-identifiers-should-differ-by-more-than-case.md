---
title: 'CA1708: Os identificadores devem ser diferentes de maiusculas e minúsculas | Microsoft Docs'
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
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 07f4b9f9a69de3458bf0f7ea7dcb316e2e9a086a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187634"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|NomeDoTipo|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Os nomes dos dois tipos, membros, parâmetros ou espaços para nomes totalmente qualificados são idênticos quando eles são convertidos em minúsculas.

## <a name="rule-description"></a>Descrição da Regra
 Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas. Por exemplo, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] é uma linguagem diferencia maiusculas de minúsculas amplamente utilizada.

 Essa regra é acionada em apenas a membros publicamente visível.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Selecione um nome exclusivo quando comparado a outros identificadores no diferenciando maiusculas de minúsculas.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. A biblioteca não pode ser utilizada em todos os idiomas disponíveis no [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="example-of-a-violation"></a>Exemplo de uma violação
 O exemplo a seguir demonstra uma violação dessa regra.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)



