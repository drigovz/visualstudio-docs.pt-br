---
title: Subir os membros
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969127"
---
# <a name="pull-members-up"></a>Subir os membros

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite que você extraia Membros para o tipo base.

**Quando:** Você implementou uma interface e deseja mover um membro para o tipo base.

**Por que:** A extração de membros permite que outras implementações da sua interface herdem esses membros também.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em qualquer membro de uma interface implementada.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Subir os membros](media/pull-members-up.png)

2. Selecione **Subir os membros até o tipo base**.

3. Na caixa de diálogo, selecione quais membros você deseja adicionar à interface selecionada.

   ![Subir os membros](media/pull-members-up-dialog.png)

4. Escolha **OK**. Os membros selecionados sobem para a interface.

   ![Ação Subir os membros concluída](media/pull-members-up-completed.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
