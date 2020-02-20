---
title: Tornar membro estático
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515298"
---
# <a name="make-member-static"></a>Tornar membro estático

Esta refatoração aplica-se a:

- C#

**O que:** Tornar um membro estático.

**Quando:** Você deseja que um membro não estático seja estático.

**Por que:** Os membros estáticos melhoram a legibilidade: saber se o código específico está isolado torna mais fácil entender, ler e reutilizar. 

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome do membro.

2. Pressione **Ctrl**+ **.** (ponto) para disparar o menu **ações rápidas e refatorar** .

   ![Tornar membro estático](media/make-member-static.png)

3. Selecione **Tornar estático**.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
