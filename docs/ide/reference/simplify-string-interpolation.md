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
ms.openlocfilehash: a8b0fd53164cb98921b111d49fa04a76c9d0d8a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094300"
---
# <a name="simplify-string-interpolation-refactoring"></a>Simplificar refatoração de interpolação de cadeia de caracteres

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite simplificar uma [interpolação de cadeia de caracteres](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Quando:** Você tem uma interpolação de cadeia de caracteres que pode ser simplificada.

**Por que:** Simplificar uma interpolação de cadeia de caracteres pode fornecer mais clareza e sintaxe concisa. Essa ferramenta de refatoração executará a tarefa automaticamente em vez de fazer isso manualmente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre a interpolação da cadeia de caracteres:

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecionar **simplificar interpolação**

    ![Simplificar a interpolação da cadeia de caracteres](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)