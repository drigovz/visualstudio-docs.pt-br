---
title: Comentários da Tarefa
description: Adicionando comentários de tarefa ao seu código
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493524"
---
# <a name="task-comments"></a>Comentários da Tarefa

Ao escrever o código, uma prática padrão é comentar explicitamente código incompleto, questionável ou soluções alternativas rápidas com avisos. Os tokens de sinal padrão fornecidos pelo Visual Studio para Mac são TODO, HACK, FIXME e UNDONE. Os tokens personalizados podem ser definidos em **Visual Studio > Preferências > Ambiente > Tarefas** , conforme ilustrado na imagem a seguir:

![Preferências da lista de tarefas](media/source-editor-image10.png)

Para adicionar um novo comentário de tarefa, adicione um comentário que inclui a palavra-chave da tarefa. Por exemplo:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio para Mac chama atenção para esses marcadores destacando-os na janela **lista de tarefas** , que pode ser exibida usando o menu **Exibir > tarefas** :

![A janela lista de tarefas, mostrando um único item TODO](media/source-editor-image11.png)

## <a name="see-also"></a>Confira também

- [Usar a Lista de Tarefas (Visual Studio no Windows)](/visualstudio/ide/using-the-task-list)