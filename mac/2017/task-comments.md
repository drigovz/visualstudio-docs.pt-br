---
title: Comentários da Tarefa
description: Adicionando comentários de tarefa ao seu código
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 4f7f3d1567972c3841af6deb37677a7e01cdb825
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985179"
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