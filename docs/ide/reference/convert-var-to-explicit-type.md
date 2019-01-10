---
title: Refatorar o código para substituir var por um tipo explícito
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 893fc2f989dab579690cdac37edae3ba0fad606a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869127"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refatorar para substituir var por um tipo explícito

Use esta refatoração para substituir [var](/dotnet/csharp/language-reference/keywords/var) em uma declaração de variável local com um tipo explícito.

Esta refatoração aplica-se a:

- C#

## <a name="why-to-use-an-explicit-type"></a>Por que usar um tipo explícito

Veja a seguir alguns motivos para declarar uma variável com um tipo explícito:

- Para melhorar a legibilidade do código.

- Quando você não quer inicializar a variável na declaração.

No entanto, é necessário usar [var](/dotnet/csharp/language-reference/keywords/var) quando uma variável é inicializada com um tipo anônimo e as propriedades do objeto são acessadas em um momento posterior. Para saber mais, confira [Variáveis locais de tipo implícito (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Como usá-lo

1. Coloque o cursor sobre a palavra-chave `var`.

1. Pressione **Ctrl**+**.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Usar o menu de ações rápidas de tipo explícito](media/use-explicit-type.png)

1. Selecione **Usar o tipo explícito**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

## <a name="see-also"></a>Consulte também

- [Variáveis tipadas implicitamente (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)