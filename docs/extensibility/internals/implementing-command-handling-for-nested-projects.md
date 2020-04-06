---
title: Implementando o manuseio de comandos para projetos aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707603"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementando a manipulação de comando para projetos aninhados
O IDE pode passar comandos <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> que <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> são passados através do e as interfaces para projetos aninhados, ou projetos-pai podem filtrar ou substituir os comandos.

> [!NOTE]
> Somente os comandos normalmente manuseados pelo projeto pai podem ser filtrados. Comandos como **Build** and **Deploy** que são manipulados pelo IDE não podem ser filtrados.

 As etapas a seguir descrevem o processo de implementação do manuseio de comandos.

## <a name="procedures"></a>Procedimentos

#### <a name="to-implement-command-handling"></a>Para implementar o manuseio de comandos

1. Quando o usuário seleciona um projeto aninhado ou um nó em um projeto aninhado:

   1. O IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chama o método.

      — ou —

   2. Se o comando se originou em uma janela de hierarquia, como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> comando de menu de atalho no Solution Explorer, o IDE chamará o método no pai do projeto.

2. O projeto pai pode examinar `QueryStatus`parâmetros `pguidCmdGroup` a `prgCmds`serem passados para, como e, para determinar se o projeto pai deve filtrar os comandos. Se o projeto pai for implementado para filtrar comandos, ele deve definir:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Em seguida, o `S_OK`projeto pai deve retornar .

    Se o projeto pai não filtrar o `S_OK`comando, ele deve apenas retornar . Neste caso, o IDE encaminha automaticamente o comando para o projeto criança.

    O projeto pai não precisa encaminhar o comando para o projeto filho. O IDE executa esta tarefa..

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Aninhando projetos](../../extensibility/internals/nesting-projects.md)
