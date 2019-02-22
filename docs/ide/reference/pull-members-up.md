---
title: Efetuar Pull de Membros Para Nível Superior
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 65ce1b44063fd6152fc300e32e7dd075fa8afcbf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335762"
---
# <a name="pull-members-up"></a>Efetuar pull de membros para nível superior

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** Permite que você efetue pull membros até o tipo base.

**Quando:** Você implementou uma interface e deseja mover um membro para o tipo base.

**Por que:** Efetuar pull de membros permite que outras implementações de sua interface também herdem esses membros.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em qualquer membro de uma interface implementada.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Efetuar pull de membros para nível superior](media/pull-members-up.png)

2. Selecione **Efetuar pull de membros até o tipo base**.

3. Na caixa de diálogo, selecione quais membros você deseja adicionar à interface selecionada.

   ![Efetuar pull de membro para nível superior](media/pull-members-up-dialog.png)

4. Escolha **OK**. É efetuado pull dos membros selecionados para a interface.

   ![Pull de membros para nível superior concluído](media/pull-members-up-completed.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
