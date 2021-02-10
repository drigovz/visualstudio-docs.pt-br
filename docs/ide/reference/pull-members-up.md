---
title: Subir os membros
description: Saiba como usar o menu ações rápidas e refatoração para efetuar pull de membros para o tipo base.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ee5776e9fc39b77f8059146848d847e0976a5664
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958278"
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

4. Selecione **OK**. Os membros selecionados sobem para a interface.

   ![Ação Subir os membros concluída](media/pull-members-up-completed.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
