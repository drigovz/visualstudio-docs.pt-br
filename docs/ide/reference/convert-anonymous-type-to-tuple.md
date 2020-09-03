---
title: Converter tipo anônimo em tupla
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
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094273"
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

   ![Converter tipo anônimo em tupla](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
