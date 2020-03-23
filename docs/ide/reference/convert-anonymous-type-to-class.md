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
ms.openlocfilehash: 2379ce588eeb4773e562f630ade37e28d7f17315
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094292"
---
# <a name="convert-anonymous-type-to-class"></a>Converter tipo anônimo em classe

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que é isso?** Converta um tipo anônimo para classe.

**Quando:** Você tem um tipo anônimo que você quer continuar a construir em uma classe.

**Por que:** Tipos anônimos são úteis se você estiver usando-os apenas localmente. À medida que o código cresce, é bom ter uma maneira fácil de promovê-los para uma classe.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em um tipo anônimo.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Converter tipo anônimo em classe](media/convert-anon-to-class.png)

2. Pressione **Enter** para aceitar a refatoração.

   ![Converter tipo anônimo em classe aceito](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
