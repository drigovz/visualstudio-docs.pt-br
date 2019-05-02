---
title: Converter tipo anônimo em tupla
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b6f5dd8e53ed2e0695370a1cdcb837609be30035
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968554"
---
# <a name="convert-anonymous-type-to-tuple"></a>Converter tipo anônimo em tupla

Esta refatoração aplica-se a:

- C#

**O quê:** Converta um tipo anônimo em tupla.

**Quando:** Você tem um tipo anônimo que é qualificado como uma tupla.

**Por que:** [Tuplas](/dotnet/csharp/tuples) são úteis para manter sua sintaxe leve. Essa ação rápida torna mais fácil aproveitar esse recurso C#.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em um tipo anônimo.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Converter tipo anônimo em tupla](media/convert-anon-to-tuple.png)

2. Pressione **Enter** para aceitar a refatoração.

   ![Converter tipo anônimo em tupla](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
