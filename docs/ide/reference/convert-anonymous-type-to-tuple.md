---
title: Converter tipo anônimo em tupla
description: Saiba como usar o menu ações rápidas e refatoração para converter um tipo anônimo em uma tupla no Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 452ba826a2765ef624e6c3d04bb20915a26c51fb
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040856"
---
# <a name="convert-anonymous-type-to-tuple"></a>Converter tipo anônimo em tupla

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Converter um tipo anônimo em tupla.

**Quando:** Você tem um tipo anônimo que se qualifica como uma tupla.

**Por que:** as [tuplas](/dotnet/csharp/tuples) são úteis para manter sua sintaxe leve. Essa ação rápida torna mais fácil aproveitar esse recurso C#.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em um tipo anônimo.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Converter tipo anônimo em tupla](media/convert-anon-to-tuple.png)

2. Pressione **Enter** para aceitar a refatoração.

   ![Converter tipo anônimo em tupla aceita](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
