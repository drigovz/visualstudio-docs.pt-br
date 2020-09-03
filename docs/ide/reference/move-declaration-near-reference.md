---
title: Mover a declaração de variável para perto da referência
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1339f4a9d151ef41d9a35c5aac0a96f220a297b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093992"
---
# <a name="move-declaration-near-reference-refactoring"></a>Mover declaração de variável para perto da referência no Visual Studio

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite mover declarações de variável mais próximo do seu uso.

**Quando:** você tem declarações de variável que podem estar em um escopo mais restrito.

**Por quê:** você pode deixá-lo como está, mas isso pode causar problemas de legibilidade ou ocultação de informações. Esta é uma chance de refatorar para melhorar a legibilidade.

## <a name="how-to"></a>Como fazer

1. coloque o cursor na declaração da variável.

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Mover declaração para próximo da referência** no pop-up da janela Visualização.
   - **Mouse**
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Mover declaração para próximo da referência** no pop-up da janela Visualização.

1. Quando estiver satisfeito com a alteração, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

Exemplo:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
