---
title: Mover a declaração de variável para perto da referência
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e23c5c8d6ea0895f9e5a78e726bb7a7cede071bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540590"
---
# <a name="move-declaration-near-reference-refactoring"></a>Mover declaração de variável para perto da referência no Visual Studio

Esta refatoração aplica-se a:

- C#

**O quê:** Permite mover declarações de variável para mais perto de seu uso.

**Quando:** Você tem declarações de variável que podem estar em um escopo mais restrito.

**Por que:** Você pode deixá-lo como está, mas isso pode causar problemas de legibilidade ou ocultação de informações. Esta é uma chance de refatorar para melhorar a legibilidade.

## <a name="how-to"></a>Como fazer

1. coloque o cursor na declaração da variável.

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Mover declaração para próximo da referência** no pop-up da janela Visualização.
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

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)