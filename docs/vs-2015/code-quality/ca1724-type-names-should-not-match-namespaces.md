---
title: 'CA1724: os nomes de tipo não devem corresponder a namespaces | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671592"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: os nomes de tipo não devem corresponder a namespaces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Categoria|Microsoft. Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um nome de tipo corresponde a um [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nomes de namespace em uma comparação que não diferencia maiúsculas de minúsculas.

## <a name="rule-description"></a>Descrição da Regra
 Os nomes de tipo não devem corresponder aos nomes de namespaces definidos na biblioteca de classes do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. A violação dessa regra pode reduzir a usabilidade da biblioteca.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Selecione um nome de tipo que não corresponda ao nome de um namespace de biblioteca de classes [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Para o novo desenvolvimento, nenhum cenário conhecido ocorre onde você deve suprimir um aviso dessa regra. Antes de suprimir o aviso, considere cuidadosamente como os usuários da biblioteca podem ser confundidos pelo nome correspondente. Para as bibliotecas de envio, talvez seja necessário suprimir um aviso dessa regra.
