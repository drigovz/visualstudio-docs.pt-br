---
title: Valores e parâmetros não utilizados
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1ea80887fff6dcb1afba80feb782b23d1e790579
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325021"
---
# <a name="unused-expression-values-and-parameters"></a>Parâmetros e valores de expressão não usados

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O quê:** Esmaece parâmetros não usados e gera um aviso para valores de expressão não usados.

**Quando:** Você tem parâmetros ou valores de expressão que nunca são usados.

**Por que:** Às vezes, é difícil dizer se um valor ou um parâmetro não está sendo mais usado. Esmaecendo esses valores ou fornecendo um aviso, você obtém uma indicação visual de qual código pode ser excluído.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnóstico de valores de expressão e parâmetros não usados

1. Ter qualquer valor de expressão ou parâmetro que não é usado.
2. O parâmetro não usado aparece esmaecido. O valor de expressão não usado recebe um aviso.

  ![Parâmetro não usado](media/unused-parameter.png)
  ![Valor não usado](media/unused-value.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
