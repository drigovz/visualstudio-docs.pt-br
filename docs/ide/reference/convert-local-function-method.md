---
title: Converter uma função local em um método
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ccddc3aef24ba14245dc568ca5f369e38ce8eba0
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531644"
---
# <a name="convert-a-local-function-to-a-method"></a>Converter uma função local em um método

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O quê:** converter uma função local em um método.

**Quando:** você tem uma função local que deseja definir fora do contexto local atual.

**Por que:** você deseja converter uma função local em um método para poder chamá-la fora do contexto local. O recomendado é converter em um método quando a função local está ficando muito longa. Ao definir a função em um método separado, seu código fica mais fácil de ler.

## <a name="convert-local-function-to-method-refactoring"></a>Refatoração de converter uma função local em um método

1. Coloque o cursor na função local.

    ![Converter uma função local em um exemplo de código de método](media/convert-local-function-to-method.png)

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Converter uma função local em um exemplo de correção de código de método](media/convert-local-function-to-method-codefix.png)

2. Pressione Enter para aceitar a refatoração.

    ![Converter a função local para um exemplo de resultado de método](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../csharp-developer-productivity.md)
