---
title: Converter tipo anônimo em classe
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: 251a011695f6f5056e1fdf8e1a6be36b898b66f5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809205"
---
# <a name="convert-anonymous-type-to-class"></a>Converter tipo anônimo em classe

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Converta um tipo anônimo em classe.

**Quando:** Você tem um tipo anônimo que deseja continuar a criar em uma classe.

**Por que:** Os tipos anônimos serão úteis se você estiver apenas usando-os localmente. À medida que o código cresce, é bom ter uma maneira fácil de promovê-los para uma classe.

## <a name="how-to"></a>Instruções

1. Coloque o cursor em um tipo anônimo.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Converter tipo anônimo em classe](media/convert-anon-to-class.png)

2. Pressione **Enter** para aceitar a refatoração.

   ![Converter tipo anônimo em classe aceito](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
