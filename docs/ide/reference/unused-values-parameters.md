---
title: Valores e parâmetros não utilizados
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
ms.openlocfilehash: 2d0875f9a298af24575cc05008713cbb6c3e2ead
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58414675"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Parâmetros, variáveis e atribuições de valor não usados

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O quê:** Esmaece parâmetros não usados e gera um aviso para valores de expressão não usados. O compilador também executa uma análise de fluxo para localizar todas as atribuições de valor não usadas. Atribuições de valor não usadas esmaecem e uma lâmpada aparece com um [Ação Rápida](../quick-actions.md) para remover a atribuição redundante. Variáveis não utilizadas com valores desconhecidos mostram uma sugestão de [Ação Rápida](../quick-actions.md) para usar [discards](/dotnet/csharp/discards) em vez disso. (Discards são variáveis temporárias e fictícias, não utilizadas intencionalmente no código do aplicativo. Eles podem reduzir a alocação de memória e facilitar a leitura do seu código.)

**Quando:** Você tem atribuições de valor, parâmetros ou valores de expressão que nunca são usados.

**Por que:** Às vezes, é difícil dizer se uma atribuição de valor, variável ou parâmetro não está mais sendo usada. Esmaecendo esses valores ou gerando um aviso, você obtém uma indicação visual de qual código pode ser excluído.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnóstico de valores de expressão e parâmetros não usados

1. Observe qualquer atribuição de valor, variável ou parâmetro que não é usado.
2. A atribuição de valor ou parâmetro não usado aparece esmaecido. O valor de expressão não usado gera um aviso.

  ![Parâmetro não usado](media/unused-parameter.png)
  ![Valor não usado](media/unused-value.png)
  ![Atribuição de valor não usada](media/unused-value-assignment.png)
  ![Discard de valor não usado](media/unused-value-discard.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
