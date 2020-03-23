---
title: Caixa de diálogo Lista de Tarefas, Ambiente, Opções
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05c337a6e809f85490e651fecf405b44e9f28930
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592003"
---
# <a name="options-dialog-box-environment--task-list"></a>Caixa de diálogo \> opções: Lista de tarefas do ambiente

Esta página Opções permite a você adicionar, excluir e alterar os tokens de comentário que geram lembretes da **Lista de Tarefas**. Para exibir essas configurações, selecione **Opções** no menu **Ferramentas**, expanda a pasta **Ambiente** e escolha **Lista de Tarefas**.

## <a name="task-list-tokens"></a>Tokens de Lista de Tarefas

Quando você inserir um comentário em seu código cujo texto começa com um token da **Lista de Tokens**, a **Lista de Tarefas** exibirá seu comentário como uma nova entrada sempre que o arquivo for aberto para edição. Clique na entrada **Lista de Tarefas** para ir diretamente para a linha de comentário em seu código. Para obter mais informações, consulte [Usando a Lista de Tarefas](../../ide/using-the-task-list.md).

Lista de Token\
Exibe uma lista de tokens e permite que você adicione ou remova tokens personalizados. Os tokens de comentário diferenciam maiúsculas de minúsculas no C# e no C++, mas não no Visual Basic.

> [!NOTE]
> Se você não digitar o token desejado exatamente como ele é exibido na lista de tokens, a tarefa de comentário não será exibida na **Lista de Tarefas**.

Prioridade\
Define a prioridade das tarefas que usam o token selecionado (baixa, normal ou alta). Os comentários de tarefa que começam com esse token recebem automaticamente a prioridade designada na **Lista de Tarefas**.

Nome\
Insira a cadeia de token aqui e, em seguida, clique em **Adicionar** para adicionar a cadeia de caracteres na lista de tokens.

Adicionar\
Habilitado quando você insere um novo **Nome**. Clique para adicionar uma nova cadeia de caracteres do token usando os valores inseridos nos campos **Nome** e **Prioridade**.

Excluir\
Clique para excluir o token selecionado da lista de tokens. Não é possível excluir o token de comentário padrão.

Alterar\
Clique para fazer alterações em um token existente usando os valores inseridos nos campos **Nome** e **Prioridade**.

> [!NOTE]
> Não é possível renomear nem excluir o token de comentário padrão, mas é possível alterar seu nível de prioridade.

## <a name="see-also"></a>Confira também

- [Usar a Lista de Tarefas](../../ide/using-the-task-list.md)
- [Definir indicadores no código](../../ide/setting-bookmarks-in-code.md)
