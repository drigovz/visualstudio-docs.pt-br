---
title: 'CA1504: Examinar nomes de campo confusos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da99bab4235028f75146be1807162e93759d3eb9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926456"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Examinar nomes de campo confusos

|||
|-|-|
|NomeDoTipo|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Categoria|Microsoft.Maintainability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 O nome de um campo de instância começa com "s _" ou o nome de um `static` (`Shared` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo começa com "m _".

## <a name="rule-description"></a>Descrição da regra
 Nomes de campo que começam com "s _" são associados a dados estáticos por muitos usuários. Da mesma forma, os nomes de campo que começam com "m _" são associados a dados da instância (membro). Para o código mais fácil manutenção, os nomes devem seguir convenções geralmente usadas.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, renomeie o campo usando o prefixo apropriado. Como alternativa, tornar o campo concordar com o sufixo atual, adicionando ou removendo o `static` modificador.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.