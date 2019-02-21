---
title: Converter tipo anônimo em classe
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3613f365b2510111f6854087a597df387ab1a4c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335744"
---
# <a name="convert-anonymous-type-to-class"></a>Converter tipo anônimo em classe

Esta refatoração aplica-se a:

- C#

**O quê:** Converta um tipo anônimo em classe.

**Quando:** Você tem um tipo anônimo que deseja que continue a se basear em uma classe.

**Por que:** Tipos anônimos são úteis se você está usando-os apenas localmente. À medida que o código cresce, é bom ter uma maneira fácil de promovê-los para uma classe.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em um tipo anônimo.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Converter tipo anônimo em classe](media/convert-anon-to-class.png)

2. Pressione **Enter** para aceitar a refatoração.

   ![Converter tipo anônimo em classe aceito](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
