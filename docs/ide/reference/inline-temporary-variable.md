---
title: Substituir uma variável temporária por seu valor
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6fea50f3cceb907cb014d29bb46988ab07dad6c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066857"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Refatoração Embutir uma variável temporária

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** Permite remover uma variável temporária e substitua-a por seu valor.

**Quando:** O uso da variável temporária dificulta o entendimento do código.

**Por que:** A remoção de uma variável temporária pode facilitar a leitura do código.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro de uma variável temporária para ser embutida:

   - C#:

       ![Código realçado – C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Código realçado – Visual Basic](media/inline-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse no código e selecione o menu **Ações e Refatorações Rápidas**.

3. Selecione **Variável temporária embutida** no pop-up da janela Visualização.

   A variável é removida e seus usos são substituídos pelo valor da variável.

   - C#:

      ![Resultado embutido – C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Resultado embutido – Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)