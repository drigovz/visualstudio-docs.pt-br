---
title: Tornar membro estático
description: Saiba como usar o menu ações rápidas e refatoração para tornar um membro estático.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5478e85d89d4ea44d34e0a5ae9170aaffb3836f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919449"
---
# <a name="make-member-static"></a>Tornar membro estático

Esta refatoração aplica-se a:

- C#

**O que:** Tornar um membro estático.

**Quando:** Você deseja que um membro não estático seja estático.

**Por que:** Os membros estáticos melhoram a legibilidade: saber se o código específico está isolado torna mais fácil entender, ler e reutilizar. 

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome do membro.

2. Pressione **Ctrl** + **.** (ponto) para disparar o menu **ações rápidas e refatorar** .

   ![Tornar membro estático](media/make-member-static.png)

3. Selecione **Tornar estático**.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
