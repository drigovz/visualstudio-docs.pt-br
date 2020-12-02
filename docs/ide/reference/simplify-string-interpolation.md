---
title: Simplificar a interpolação da cadeia de caracteres
description: Saiba como usar o menu ações rápidas e refatoração para simplificar uma interpolação de cadeia de caracteres.
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
ms.openlocfilehash: 422e3f24b98fd1ddd155e5c3975833b4e4cb248c
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479934"
---
# <a name="simplify-string-interpolation-refactoring"></a>Simplificar refatoração de interpolação de cadeia de caracteres

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite simplificar uma [interpolação de cadeia de caracteres](/dotnet/csharp/tutorials/string-interpolation).

**Quando:** Você tem uma interpolação de cadeia de caracteres que pode ser simplificada.

**Por que:** Simplificar uma interpolação de cadeia de caracteres pode fornecer mais clareza e sintaxe concisa. Essa ferramenta de refatoração executará a tarefa automaticamente em vez de fazer isso manualmente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre a interpolação da cadeia de caracteres:

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecionar **simplificar interpolação**

    ![Simplificar a interpolação da cadeia de caracteres](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)