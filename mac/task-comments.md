---
title: Comentários da Tarefa
description: Adicionando comentários de tarefa ao seu código
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692321"
---
# <a name="task-comments"></a>Comentários da Tarefa

Ao escrever o código, uma prática padrão é comentar explicitamente código incompleto, questionável ou soluções alternativas rápidas com avisos. Os tokens de sinal padrão fornecidos pelo Visual Studio para Mac são TODO, HACK, FIXME e UNDONE. Os tokens personalizados podem ser definidos em **Visual Studio > Preferências > Ambiente > Tarefas**, conforme ilustrado na imagem a seguir:

![Preferências da lista de tarefas](media/source-editor-image10.png)

Para adicionar um novo comentário de tarefa, adicione um comentário que inclui a palavra-chave da tarefa. Por exemplo:

```csharp
//TODO: Finish this for all properties.
```

O Visual Studio para Mac chama a atenção para esses marcadores realçando-os no painel da **Lista de Tarefas**, que pode ser exibido navegando para **Exibir > Painéis > Tarefa**:

![Painel de lista de tarefas](media/source-editor-image11.png)

## <a name="see-also"></a>Consulte também

- [Usar a Lista de Tarefas (Visual Studio no Windows)](/visualstudio/ide/using-the-task-list)