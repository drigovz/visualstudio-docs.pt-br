---
title: Simplificar a interpolação da cadeia de caracteres
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
ms.openlocfilehash: 5e801d417280d5d9ce8225c2185b582544fe2cef
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810331"
---
# <a name="simplify-string-interpolation-refactoring"></a>Simplificar refatoração de interpolação de cadeia de caracteres

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite simplificar uma [interpolação de cadeia de caracteres](/dotnet/csharp/tutorials/string-interpolation).

**Quando:** Você tem uma interpolação de cadeia de caracteres que pode ser simplificada.

**Por que:** Simplificar uma interpolação de cadeia de caracteres pode fornecer mais clareza e sintaxe concisa. Essa ferramenta de refatoração executará a tarefa automaticamente em vez de fazer isso manualmente.

## <a name="how-to"></a>Instruções

1. Coloque o cursor sobre a interpolação da cadeia de caracteres:

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecionar **simplificar interpolação**

    ![Simplificar a interpolação da cadeia de caracteres](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)