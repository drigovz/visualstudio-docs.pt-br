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
ms.openlocfilehash: afcf85fff188853890b86cf7deb13b2457f5e0b8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157692"
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
