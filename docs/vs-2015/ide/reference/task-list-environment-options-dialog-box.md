---
title: Caixa de diálogo Lista de Tarefas, Ambiente, Opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72e5f82fa3ca4b7ca909ee07e5b77a31b3e20879
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650973"
---
# <a name="task-list-environment-options-dialog-box"></a>Caixa de diálogo Lista de Tarefas, Ambiente, Opções
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta página Opções permite a você adicionar, excluir e alterar os tokens de comentário que geram lembretes da **Lista de Tarefas**. Para exibir essas configurações, selecione **Opções** no menu **Ferramentas**, expanda a pasta **Ambiente** e escolha **Lista de Tarefas**.

## <a name="task-list-options"></a>Opções da Lista de Tarefas
 Confirmar a exclusão de tarefas quando selecionado, uma caixa de mensagem é exibida sempre que uma tarefa de usuário é excluída da **lista de tarefas**, permitindo que você confirme a exclusão. Essa opção é habilitada por padrão.

> [!NOTE]
> Para excluir um Comentário de Tarefa, use o link para localizar o comentário e, em seguida, remova-o do seu código.

 Mostrar nomes de arquivos somente quando selecionado, a coluna **arquivo** da **lista de tarefas** exibe somente os nomes dos arquivos a serem editados, não seus caminhos completos.

## <a name="tokens"></a>Tokens
 Quando você inserir um comentário em seu código cujo texto começa com um token na **Lista de Tokens**, a **Lista de Tarefas** exibirá seu comentário como nova entrada sempre que o arquivo for aberto para edição. É possível clicar nessa entrada **Lista de Tarefas** para ir diretamente para a linha de comentário no seu código. Para obter mais informações, consulte [Usando a Lista de Tarefas](../../ide/using-the-task-list.md).

 Lista de tokens exibe uma lista de tokens e permite que você adicione ou remova tokens personalizados. Tokens de comentário diferenciam maiúsculas de minúsculas no Visual C# e no Visual C++, mas não no Visual Basic.

> [!NOTE]
> Se você não digitar o token desejado exatamente como ele é exibido na **Lista de Tokens**, uma tarefa de comentário não será exibida na **Lista de Tarefas**.

 Priority define a prioridade das tarefas que usam o token selecionado. Os comentários de tarefa que começam com esse token recebem automaticamente a prioridade designada na **Lista de Tarefas**.

 Nome Insira a cadeia de caracteres do token. Isso habilita o botão **Adicionar**. Em **Adicionar**, essa cadeia de caracteres é incluída na **Lista de Tokens**, e os comentários que começam com esse nome serão exibidos na **Lista de Tarefas**.

 Adicione habilitado quando você inserir um novo **nome**. Clique para adicionar uma nova cadeia de caracteres do token usando os valores inseridos nos campos **Nome** e **Prioridade**.

 Excluir Clique para excluir o token selecionado da **lista de tokens**. Não é possível excluir o token de comentário padrão.

 Alterar clique para fazer alterações em um token existente usando os valores inseridos nos campos **nome** e **prioridade** .

> [!NOTE]
> Não é possível renomear nem excluir o token de comentário padrão, mas é possível alterar seu nível de prioridade.

## <a name="see-also"></a>Consulte Também
 [Usando o lista de tarefas](../../ide/using-the-task-list.md) [definir indicadores na caixa de](../../ide/setting-bookmarks-in-code.md) [diálogo opções de ambiente](../../ide/reference/environment-options-dialog-box.md) de código
