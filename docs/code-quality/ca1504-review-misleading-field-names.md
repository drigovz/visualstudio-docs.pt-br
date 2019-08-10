---
title: 'CA1504: Examinar nomes de campo confusos'
ms.date: 11/04/2016
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
ms.openlocfilehash: df6ab704c2dfdbf8ebdf8eb42f56d8d64600736f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921821"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Examinar nomes de campo confusos

|||
|-|-|
|NomeDoTipo|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Categoria|Microsoft.Maintainability|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
O nome de um campo de instância começa com "s_" ou o nome de `static` um`Shared` campo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)](in) começa com "M_".

## <a name="rule-description"></a>Descrição da regra
Os nomes de campo que começam com "s_" são associados a dados estáticos por muitos usuários. Da mesma forma, os nomes de campo que começam com "M_" são associados a dados de instância (membro). Para um código mais fácil de ser mantido, os nomes devem seguir as convenções geralmente usadas.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, renomeie o campo usando o prefixo apropriado. Como alternativa, faça com que o campo concorde com o sufixo atual adicionando ou removendo o `static` modificador.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.