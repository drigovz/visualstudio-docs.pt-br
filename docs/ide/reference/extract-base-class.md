---
title: Extrair classe base
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8c389ac6285b3f20dcdf05833f1ff3202d155c4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962802"
---
# <a name="extract-base-class"></a>Extrair classe base

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Extrair classe base.

**Quando:** Você deseja extrair membros de uma classe selecionada para uma nova classe base.

**Por que:** O pull manual dos membros pode ser demorado e levar você fora do seu fluxo de trabalho. 

## <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre o nome da classe ou um membro realçado.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecione **Efetuar pull de membros até a nova classe base**.

    ![Caixa de diálogo extrair classe base](media/extract-base-class.png)

A nova caixa de diálogo **Extrair Classe Base** será aberta, onde você poderá especificar o nome da classe base e o local onde ela deve ser colocada. Você pode selecionar os membros que deseja transferir para a nova classe base e optar por tornar os membros abstratos marcando a caixa de seleção na coluna tornar abstrato.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
