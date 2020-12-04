---
title: Valores e parâmetros não utilizados
description: Saiba mais sobre atribuições de valor não utilizado, variáveis e parâmetros e como eles aparecem no editor de código no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8768992ce3ef9f40ab0adba1724d43b32e5bde5c
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560701"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Parâmetros, variáveis e atribuições de valor não usados

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O que:** Esmaece os parâmetros não utilizados e gera um aviso para valores de expressão não utilizados. O compilador também executa uma análise de fluxo para localizar todas as atribuições de valor não usadas. Atribuições de valor não usadas esmaecem e uma lâmpada aparece com um [Ação Rápida](../quick-actions.md) para remover a atribuição redundante. Variáveis não utilizadas com valores desconhecidos mostram uma sugestão de [Ação Rápida](../quick-actions.md) para usar [discards](/dotnet/csharp/discards) em vez disso. (Discards são variáveis temporárias e fictícias, não utilizadas intencionalmente no código do aplicativo. Eles podem reduzir a alocação de memória e facilitar a leitura do seu código.)

**Quando:** Você tem atribuições de valor, parâmetros ou valores de expressão que nunca são usados.

**Por que:** Às vezes, é difícil dizer se uma atribuição de valor, variável ou parâmetro não está mais sendo usado. Esmaecendo esses valores ou gerando um aviso, você obtém uma indicação visual de qual código pode ser excluído.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnóstico de valores de expressão e parâmetros não usados

1. Observe qualquer atribuição de valor, variável ou parâmetro que não é usado.
2. A atribuição de valor não utilizado ou o parâmetro aparece desbotado. O valor da expressão não utilizada gera um aviso.

  ![Parâmetro não usado](media/unused-parameter.png)
  ![Valor não usado](media/unused-value.png)
  ![Atribuição de valor não usada](media/unused-value-assignment.png)
  ![Discard de valor não usado](media/unused-value-discard.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
