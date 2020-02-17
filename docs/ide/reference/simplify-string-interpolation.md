---
title: Simplificar interpolação de cadeia de caracteres
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 15f034b0ecf46e19681f3b74e4137a2de9e9d950
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280750"
---
# <a name="simplify-string-interpolation-refactoring"></a>Simplificar refatoração de interpolação de cadeia de caracteres

Esta refatoração aplica-se a:

- C#

**O que:** Permite simplificar uma [interpolação de cadeia de caracteres](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Quando:** Você tem uma interpolação de cadeia de caracteres que pode ser simplificada.

**Por que:** Simplificar uma interpolação de cadeia de caracteres pode fornecer mais clareza e sintaxe concisa. Essa ferramenta de refatoração executará a tarefa automaticamente em vez de fazer isso manualmente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre a interpolação da cadeia de caracteres:

2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecionar **simplificar interpolação**

    ![Simplificar interpolação de cadeia de caracteres](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)