---
title: 'Como: Gerenciando vários threads em código gerenciado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702774"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Como: Gerenciar vários segmentos em código gerenciado
Se você tiver uma extensão VSPackage gerenciada que chame métodos assíncronos ou tenha operações que executem em outros segmentos além do segmento Visual Studio UI, você deve seguir as diretrizes dadas abaixo. Você pode manter o segmento de ia responsivo porque não precisa esperar o trabalho em outro segmento para ser concluído. Você pode tornar seu código mais eficiente, porque você não tem threads extras que tomam espaço de pilha, e você pode torná-lo mais confiável e mais fácil de depurar porque você evita impasses e travas.

 Em geral, você pode mudar do segmento de IA para um segmento diferente, ou vice-versa. Quando o método retorna, o segmento atual é o segmento do qual foi originalmente chamado.

> [!IMPORTANT]
> As seguintes diretrizes usam <xref:Microsoft.VisualStudio.Threading> as APIs no <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> namespace, em particular, a classe. As APIs neste namespace [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]são novas em . Você pode obter uma <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> instância <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`de um da propriedade.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Mude do segmento de ia para um segmento de plano de fundo

1. Se você estiver no segmento de ia e quiser fazer um trabalho `Task.Run()`assíncrono em um segmento de fundo, use:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Se você estiver no segmento de ia de ui e quiser bloquear sincronizadamente <xref:System.Threading.Tasks.TaskScheduler> enquanto estiver executando o trabalho em um segmento de fundo, use a propriedade `TaskScheduler.Default` dentro <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Mude de um segmento de fundo para o segmento de IA

1. Se você estiver em um segmento de fundo e quiser fazer <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>algo no segmento de ia de ida e volta, use:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Você pode <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> usar o método para mudar para o segmento de ia. Este método posta uma mensagem para o segmento de IA com a continuação do método assíncrono atual, e também se comunica com o resto da estrutura de rosca para definir a prioridade correta e evitar impasses.

     Se o seu método de segmento de fundo não for assíncrono e você `await` não puder torná-lo assíncrono, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>você ainda pode usar a sintaxe para mudar para o segmento de UI, envolvendo seu trabalho com , como neste exemplo:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
