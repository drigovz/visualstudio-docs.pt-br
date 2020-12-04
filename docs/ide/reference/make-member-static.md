---
title: Tornar membro estático
description: Saiba como usar o menu ações rápidas e refatoração para tornar um membro estático.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e663d59f47728bc4a7c84290ee0e89ae453f23ae
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561013"
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
