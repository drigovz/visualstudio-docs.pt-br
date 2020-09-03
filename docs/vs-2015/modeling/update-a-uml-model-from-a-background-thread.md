---
title: Atualizar um modelo UML de um thread em segundo plano | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e6626faa09f1e38506c2d205d13caa9a3707fc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659460"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Atualizar um modelo UML por meio de um thread em segundo plano
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Às vezes, pode ser útil fazer alterações em um modelo em um thread em segundo plano. Por exemplo, se você estiver carregando informações de um recurso externo lento, poderá usar um thread em segundo plano para supervisionar as atualizações. Isso permite que o usuário veja cada atualização assim que ela acontece.

 No entanto, você deve estar ciente de que o repositório UML não é thread-safe. As seguintes precauções são importantes:

- Cada atualização de um modelo ou diagrama deve ser feita no thread da interface do usuário. O thread em segundo plano deve usar <xref:System.Windows.Forms.Control.Invoke%2A> ou `Dispatcher.` <xref:System.Windows.Threading.Dispatcher.Invoke%2A> para que o thread da interface do usuário execute as atualizações reais.

- Se você agrupar uma série de alterações em uma única transação, recomendamos impedir que o usuário edite o modelo enquanto a transação estiver em andamento. Caso contrário, as edições feitas pelo usuário se tornarão parte da mesma transação. Você pode impedir que o usuário faça alterações mostrando uma caixa de diálogo modal. Se desejar, você pode fornecer um botão Cancelar na caixa de diálogo. O usuário pode ver as alterações conforme elas acontecem.

## <a name="example"></a>Exemplo
 Este exemplo usa um thread em segundo plano para fazer várias alterações em um modelo. Uma caixa de diálogo é usada para excluir o usuário enquanto o thread está em execução. Neste exemplo simples, nenhum botão Cancelar é fornecido na caixa de diálogo. No entanto, seria fácil adicionar esse recurso.

#### <a name="to-run-the-example"></a>Para executar o exemplo

1. Crie um manipulador de comandos em um projeto C#, conforme descrito em [definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

2. Certifique-se de que o projeto inclui referências a esses assemblies:

   - Microsoft. VisualStudio. ArchitectureTools. Extensibility

   - Microsoft. VisualStudio. Modeling. Sdk. versão

   - Microsoft. VisualStudio. Modeling. Sdk. Diagrams. versão

   - Microsoft. VisualStudio. Uml. interfaces

   - System. ComponentModel. composição

   - System.Windows.Forms

3. Adicione ao projeto um formulário do Windows chamado **ProgressForm**. Ele deve exibir uma mensagem que indica que as atualizações estão em andamento. Ele não precisa ter outros controles.

4. Adicione um arquivo C# que contém o código que é mostrado após a etapa 7.

5. Compile e execute o projeto.

    Uma nova instância do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] será iniciada no modo experimental.

6. Crie ou abra um diagrama de classe UML na instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

7. Clique com o botão direito do mouse em qualquer lugar no diagrama de classe UML e clique em **Adicionar várias classes UML**.

   Várias novas caixas de classe serão exibidas no diagrama, uma após a outra em intervalos de meio segundo.

```csharp
using System;
using System.ComponentModel;
using System.ComponentModel.Composition;
using System.Threading;
using System.Windows.Forms;

using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.Uml.Classes;

namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class UmlClassAdderCommand : ICommandExtension
  {

    [Import]
    IDiagramContext context { get; set; }

    [Import]
    ILinkedUndoContext linkedUndoContext { get; set; }

    // Called when the user runs the command.
    public void Execute(IMenuCommand command)
    {
      // The form that will exclude the user.
      ProgressForm form = new ProgressForm();

      // System.ComponentModel.BackgroundWorker is a
      // convenient way to run a background thread.
      BackgroundWorker worker = new BackgroundWorker();
      worker.WorkerSupportsCancellation = true;

      worker.DoWork += delegate(object sender, DoWorkEventArgs args)
      {
        // This block will be executed in a background thread.

        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;
        IModelStore store = diagram.ModelStore;
        const int CLASSES_TO_CREATE = 15;

        // Group all the changes together.
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))
        {
          for (int i = 1; i < CLASSES_TO_CREATE; i++)
          {
            if (worker.CancellationPending)
               return; // No commit - undo all.

            // Create model elements using the UI thread by using
            // the Invoke method on the progress form. Always
            // modify the model and diagrams from a UI thread.
            form.Invoke((MethodInvoker)(delegate
            {
              IClass newClass = store.Root.CreateClass();
              newClass.Name = string.Format("NewClass{0}", i);
              diagram.Display(newClass);
            }));

            // Sleep briefly so that we can watch the updates.
            Thread.Sleep(500);
          }

          // Commit the transaction or it will be rolled back.
          transaction.Commit();
        }
      };

      // Close the form when the thread completes.
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)
      {
        form.Close();
      };

      // Start the thread before showing the modal progress dialog.
      worker.RunWorkerAsync();

      // Show the form modally, parented on VS.
      // Prevents the user from making changes while in progress.
      form.ShowDialog();
    }

    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }

    public string Text
    {
      get { return "Add several classes"; }
    }
  }
}
```

#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Para permitir que o usuário cancele o thread no exemplo

1. Adicione um botão cancelar à caixa de diálogo de progresso.

2. Adicione o seguinte código à caixa de diálogo progresso:

     `public event MethodInvoker Cancel;`

     `private void CancelButton_Click(object sender, EventArgs e)`

     `{`

     `Cancel();`

     `}`

3. No método Execute (), insira esta linha após a construção do formulário:

     `form.Cancel += delegate() { worker.CancelAsync(); };`

### <a name="other-methods-of-accessing-the-ui-thread"></a>Outros métodos de acessar o thread da interface do usuário
 Se você não quiser criar uma caixa de diálogo, poderá acessar o controle que exibe o diagrama:

 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`

 Você pode usar `uiThreadHolder.Invoke()` o para executar operações no thread da interface do usuário.

## <a name="see-also"></a>Consulte Também
 [Definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definir um manipulador de gestos em um diagrama de modelagem](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
