---
title: Sincronizar namespace e nome da pasta
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d7073edaf6ecc261c58bf1e5607323b9214c5ed0
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160752"
---
# <a name="sync-namespace-and-folder-name"></a>Sincronizar namespace e nome da pasta

Esta refatoração aplica-se a:

- C#

**O quê:** Sincronizar namespace e nome da pasta.

**Quando:** Você deseja refazer partes da sua solução arrastando um arquivo para uma nova pasta. 

**Por que:** Você deseja se certificar de que seu namespace se mantenha atualizado com a nova estrutura de pasta.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome do namespace.
2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Alterar namespace para \<nome da pasta >** .

   ![Sincronizar namespace e nome da pasta](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
