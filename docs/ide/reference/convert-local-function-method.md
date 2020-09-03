---
title: Converter uma função local em um método
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71301688"
---
# <a name="convert-a-local-function-to-a-method"></a>Converter uma função local em um método

Esta refatoração aplica-se a:

- C#

**O que:** Converta uma função local em um método.

**Quando:** Você tem uma função local que deseja definir fora do seu contexto local atual.

**Por que:** Você deseja converter uma função local em um método para que você possa chamá-la fora do contexto local. O recomendado é converter em um método quando a função local está ficando muito longa. Ao definir a função em um método separado, seu código fica mais fácil de ler.

## <a name="convert-local-function-to-method-refactoring"></a>Refatoração de converter uma função local em um método

1. Coloque o cursor na função local.

    ![Converter uma função local em um exemplo de código de método](media/convert-local-function-to-method.png)

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Converter uma função local em um exemplo de correção de código de método](media/convert-local-function-to-method-codefix.png)

2. Pressione Enter para aceitar a refatoração.

    ![Converter a função local para um exemplo de resultado de método](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
