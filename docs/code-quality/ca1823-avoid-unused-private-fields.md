---
title: 'CA1823: Evitar campos particulares não utilizados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47a2ad3b64055584551a63a2333e29286783d8cf
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921352"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitar campos particulares não utilizados

|||
|-|-|
|NomeDoTipo|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Essa regra é relatada quando um campo privado em seu código existe, mas não é usado por nenhum caminho de código.

## <a name="rule-description"></a>Descrição da regra
Foram detectados campos particulares que aparentemente não são acessados no assembly.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova o campo ou adicione o código que o utiliza.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra.

## <a name="related-rules"></a>Regras relacionadas
[CA1812: Evitar classes internas não instanciadas](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)

[CA1811: Evitar código particular não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)