---
title: Converter uma função local em um método
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 55c82aa896de5c3f3bf18468a1da98253a3def74
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324671"
---
# <a name="convert-local-function-to-method"></a>Converter uma função local em um método

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O quê:** Converter uma função local em um método

**Quando:** Você tem uma função local que deseja definir fora do contexto local atual.

**Por que:** O ideal é converter uma função local em um método para que você possa chamá-la fora do contexto local. O recomendado é converter em um método quando a função local está ficando muito longa. A definição dela em um método separado facilita a leitura do código.

## <a name="convert-local-function-to-method-refactoring"></a>Refatoração de converter uma função local em um método

1. Coloque o cursor em uma função local.

    ![Converter uma função local em um método](media/convert-local-function-to-method.png)

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Converter uma função local em uma correção de código de método](media/convert-local-function-to-method-codefix.png)

2. Pressione **Enter** para aceitar a refatoração.

    ![Converter uma função local em um resultado de método](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
