---
title: Alterar assinatura do método
description: Remover ou alterar a ordem dos parâmetros de um método. Clique com o botão direito do mouse no método, selecione Ações Rápidas e Refatorações e selecione Alterar Assinatura.
ms.date: 01/26/2018
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68711259"
---
# <a name="change-a-method-signature-refactoring"></a>Refatoração Alterar uma assinatura de método

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite remover ou alterar a ordem dos parâmetros do método.

**Quando:** você deseja mover ou remover um parâmetro de método que está sendo usado em uma variedade de locais.

**Por quê:** você pode manualmente remover e reordenar os parâmetros e, em seguida, localizar todas as chamadas para esse método e alterá-las uma por uma, mas isso poderia levar a erros.  Essa ferramenta de refatoração executará a tarefa automaticamente.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro do nome do método para modificar, ou um de seus usos:

   - C#:

       ![Código em C# realçado](media/changesignature-highlight-cs.png)

   - VB:

       ![Código em Visual Basic realçado](media/changesignature-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl+R**, em seguida, **Ctrl+V**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Alterar Assinatura** no pop-up da janela Visualização.
   - **Mouse**
      - Selecione **Editar > Refatorar > Remover Parâmetros**.
      - Selecione **Editar > Refatorar > Reordenar Parâmetros**.
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Alterar Assinatura** no pop-up da janela Visualização.

3. Na caixa de diálogo **Alterar Assinatura** que aparecer, você pode usar os botões à direita para alterar a assinatura do método:

   ![Caixa de diálogo Alterar Assinatura](media/changesignature-dialog-cs.png)

   | Botão | Descrição
   | ------ | ---
   | **Para cima/baixo** | Mova o parâmetro selecionado para cima e para baixo na lista
   | **Remover** | Remova o parâmetro selecionado da lista
   | **Restauração** | Restaurar o parâmetro selecionado e riscado na lista

   > [!TIP]
   > Use a **caixa de seleção de alterações** de referência da visualização para ver qual será o [resultado](../../ide/preview-changes.md) antes de se comprometer com ele.

4. Quando tiver terminado, pressione o botão **OK** para fazer as alterações.

   - C#:

      ![Resultado da alteração de assinatura – C#](media/changesignature-result-cs.png)

   - Visual Basic:

      ![Resultado da alteração de assinatura – Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)