---
title: Refatoração Remover código inacessível no Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: dd06fb7cd7b0e31df777a488c34a59e5a036e3b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836379"
---
# <a name="remove-unreachable-code-refactoring"></a>Refatoração Remover código inacessível

Esta refatoração aplica-se a:

- C#

**O quê:** remove o código que nunca será executado.

**Quando:** seu programa não tem um caminho para um snippet de código, tornando esse snippet de código desnecessário.

**Por quê:** melhorar a legibilidade e a facilidade de manutenção removendo o código que é supérfluo e nunca será executado.

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