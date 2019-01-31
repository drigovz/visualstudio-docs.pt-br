---
title: Refatoração Remover código inacessível
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 89b203dfb0e8f748f1e6ec11ba3c15927ee669d2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917039"
---
# <a name="remove-unreachable-code-refactoring"></a>Refatoração Remover código inacessível

Esta refatoração aplica-se a:

- C#

**O quê:** Remove o código que nunca será executado.

**Quando:** Seu programa não tem um caminho para um snippet de código, tornando esse snippet de código desnecessário.

**Por que:** Melhorar a legibilidade e a facilidade de manutenção removendo o código que é supérfluo e nunca será executado.

## <a name="how-to"></a>Como fazer

1. coloque o cursor em qualquer lugar no código esmaecido que está inacessível:

![Código inacessível esmaecido](media/unreachablecode-faded-cs.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Remover código inacessível** no pop-up da janela Visualização.
   - **Mouse**
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Remover código inacessível** no pop-up da janela Visualização.

1. Quando estiver satisfeito com a alteração, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

Exemplo:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)