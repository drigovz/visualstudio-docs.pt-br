---
title: 'CA1823: Evitar campos privados não usados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 32bf1596e4994f3cfdb2df179bb5d7f1a743f289
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201651"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitar campos particulares não utilizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Essa regra é relatada quando um campo particular em seu código existe, mas não é usado por qualquer caminho de código.

## <a name="rule-description"></a>Descrição da Regra
 Foram detectados campos particulares que aparentemente não são acessados no assembly.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o campo ou adicionar código que o usa.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1812: Evite classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)
