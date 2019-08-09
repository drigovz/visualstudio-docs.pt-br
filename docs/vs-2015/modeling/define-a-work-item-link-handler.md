---
title: Definir um manipulador de link de item de trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 240f143015f22435deb4f1347f74bebcc8b334c3
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871911"
---
# <a name="define-a-work-item-link-handler"></a>Definir um manipulador de link de item de trabalho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode criar uma extensão de integração do Visual Studio que responde quando o usuário cria ou exclui um link entre um elemento de modelo UML e um item de trabalho. Por exemplo, quando o usuário opta por vincular um novo item de trabalho a um elemento de modelo, seu código pode inicializar os campos do item de trabalho a partir de valores no modelo.

## <a name="set-up-a-uml-extension-solution"></a>Configurar uma solução de extensão UML
 Isso permitirá que você desenvolva manipuladores e, em seguida, distribua-os para outros usuários. Você precisa configurar dois projetos do Visual Studio:

- Um projeto de biblioteca de classes que contém o código do manipulador de link.

- Um projeto VSIX, que atua como um contêiner para instalar o comando. Se desejar, você pode incluir outros componentes no mesmo VSIX.

#### <a name="to-set-up-the-visual-studio-solution"></a>Para configurar a solução do Visual Studio

1. Crie um projeto de biblioteca de classes, adicionando-o a uma solução VSIX existente ou criando uma nova solução.

    1. No menu **Arquivo**, escolha **Novo**, **Projeto**.

    2. Em **modelos instalados**, expanda **Visual C#**  ou **Visual Basic**e, em seguida, na coluna do meio, clique em **biblioteca de classes**.

    3. Defina a **solução** para indicar se você deseja criar uma nova solução ou adicionar um componente a uma solução VSIX que você já abriu.

    4. Defina o nome do projeto e o local e clique em OK.

2. A menos que sua solução já contenha uma, crie um projeto VSIX.

    1. No **Gerenciador de soluções**, no menu de atalho da solução, escolha **Adicionar**, **novo projeto**.

    2. Em **modelos instalados**, expanda **Visual C#**  ou **Visual Basic**e, em seguida, selecione **extensibilidade**. Na coluna do meio, escolha **projeto VSIX**.

3. Defina o projeto VSIX como o projeto de inicialização da solução.

    - No Gerenciador de Soluções, no menu de atalho do projeto VSIX, escolha **definir como projeto de inicialização**.

4. Em **Source. Extension. vsixmanifest**, em **Content**, adicione o projeto de biblioteca de classes como um componente do MEF.

    1. Na guia **metadados** , defina um nome para o VSIX.

    2. Na guia **instalar destinos** , defina as versões do Visual Studio como os destinos.

    3. Na guia **ativos** , escolha um **novo**e, na caixa de diálogo, defina:

         Tipo = de**componente MEF**

         Origem = **de um projeto na solução atual**

         Projetar = *seu projeto de biblioteca de classes*

## <a name="defining-the-work-item-link-handler"></a>Definindo o manipulador de link de item de trabalho
 Execute todas as tarefas a seguir no projeto de biblioteca de classes.

### <a name="project-references"></a>Referências de Projeto
 Adicione os seguintes [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] assemblies às referências do projeto:

 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`

 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

 `Microsoft.VisualStudio.Uml.Interfaces`

 `System.ComponentModel.Composition`

 `System.Drawing`-usado pelo código de exemplo

 Se você não encontrar uma dessas referências na guia **.net** da caixa de diálogo **Adicionar referência** , use a guia Procurar para encontrá-la em \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies\\.

### <a name="import-the-work-item-namespace"></a>Importar o namespace do item de trabalho
 Em suas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **referências**de projeto, adicione referências aos seguintes assemblies:

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll

  No código do programa, importe os seguintes namespaces:

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;
```

### <a name="define-the-linked-work-item-event-handler"></a>Definir o manipulador de eventos de item de trabalho vinculado
 Adicione um arquivo de classe ao projeto de biblioteca de classes e defina seu conteúdo da seguinte maneira. Altere o namespace e os nomes de classe para o que preferir.

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;

namespace WorkItems
{
  [Export(typeof(ILinkedWorkItemExtension))]
  public class MyWorkItemExtension : ILinkedWorkItemExtension
  {
    // Called before a new work item is edited by the user.
    // Use this to initialize work item fields from the model element.
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)
    {
      INamedElement namedElement =
            elementsToBeLinked.First() as INamedElement;
      if (namedElement != null)
        workItemDocument.Item.Title = namedElement.Name;

    }

    // Called when any work item is linked to a model element.
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)
    {
      foreach (IElement element in elements)
        foreach (IShape shape in element.Shapes())
          shape.Color = System.Drawing.Color.Red;
    }

    // Called when a work item is unlinked from a model element.
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)
    {
      foreach (IShape shape in element.Shapes())
        shape.Color = System.Drawing.Color.White;
    }
  }
}
```

## <a name="testing-the-link-handler"></a>Testando o manipulador de link
 Para fins de teste, execute o manipulador de links no modo de depuração.

> [!WARNING]
> Você já deve estar conectado ao SCC (controle de código-fonte) do TFS para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão com um outro TFS SCC, o Visual Studio fechará a solução atual automaticamente. Verifique se você já está conectado ao SCC apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos de menu não estarão disponíveis se você não estiver conectado a um SCC.

#### <a name="to-test-the-link-handler"></a>Para testar o manipulador de link

1. Pressione **F5**ou, no menu **depurar** , escolha **Iniciar Depuração**.

     Uma instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é iniciada.

     **Solução de problemas**: Se um novo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] não for iniciado, verifique se o projeto VSIX está definido como o projeto de inicialização da solução.

2. Em experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra ou crie um projeto de modelagem e abra ou crie um diagrama de modelagem.

3. Crie um elemento de modelo, como classe UML, e defina seu nome.

4. Clique com o botão direito do mouse no elemento e clique em **Criar item de trabalho**.

    - Se o submenu mostrar a **conexão abrir Team Foundation Server**, você precisará fechar o projeto, conectar-se ao TFS apropriado e reiniciar esse procedimento.

    - Se o submenu mostrar uma lista de tipos de itens de trabalho, clique em um.

         Um novo formulário de item de trabalho é aberto.

5. Verifique se o título do item de trabalho é o mesmo que o elemento de modelo, se você tiver usado o código de exemplo na seção anterior. Isso demonstra `OnWorkItemCreated()` que funcionou.

6. Preencha o formulário, salve e feche o item de trabalho.

7. Verifique se o item de trabalho agora está em vermelho colorido. Isso demonstra `OnWorkItemLinked()` o código de exemplo.

     **Solução de problemas**: Se os métodos do manipulador não tiverem sido executados, verifique se:

    - O projeto de biblioteca de classes é listado como um componente MEF na lista de **conteúdo** em **Source. Extensions. manifest** no projeto VSIX.

    - O atributo `Export` correto é anexado à classe de manipulador e a classe implementa. `ILinkedWorkItemExtension`

    - Os parâmetros de todos `Import` os `Export` atributos e são válidos.

## <a name="about-the-work-item-handler-code"></a>Sobre o código do manipulador de item de trabalho

### <a name="listening-for-new-work-items"></a>Ouvindo novos itens de trabalho
 `OnWorkItemCreated`é chamado quando o usuário escolhe criar um novo item de trabalho a ser vinculado aos elementos do modelo. Seu código pode inicializar os campos de item de trabalho. O item de trabalho é apresentado ao usuário, que pode atualizar os campos e salvar o item de trabalho. O link para um elemento de modelo não é criado até que o item de trabalho tenha sido salvo com êxito.

```
public void OnWorkItemCreated(
    IEnumerable<IElement> elementsToBeLinked,
    IWorkItemDocument workItem)
{
  INamedElement namedElement =
         elementsToBeLinked.First() as INamedElement;
  if (namedElement != null)
      workItem.Item.Title = namedElement.Name;
}
```

### <a name="listening-for-link-creation"></a>Ouvindo a criação do link
 `OnWorkItemLinked`é chamado logo após a criação de um link. É chamado se o link é para um novo item de trabalho ou um item existente. Ele é chamado uma vez para cada item de trabalho.

```
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  foreach (IElement element in elements)
    foreach (IShape shape in element.Shapes())
         shape.Color = System.Drawing.Color.Red;
}
```

> [!NOTE]
> Para fazer este exemplo funcionar, você deve adicionar uma referência de projeto `System.Drawing.dll`a e importar o namespace `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. No entanto, essas adições não são necessárias para outras `OnWorkItemLinked`implementações do.

### <a name="listening-for-link-removal"></a>Ouvindo a remoção do link
 `OnWorkItemRemoved`é chamado uma vez antes de cada link de item de trabalho que é excluído. Se um elemento de modelo for excluído, todos os seus links serão removidos.

```
public void OnWorkItemRemoved
         (IElement element, string serverUri, int workItemId)
{...}
```

## <a name="updating-a-work-item"></a>Atualizando um item de trabalho
 Usando os namespaces do Team Foundation, você pode manipular um item de trabalho.

 Para usar o exemplo a seguir, adicione esses assemblies do .NET às referências do seu projeto:

- Microsoft.TeamFoundation.Client.dll

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

```

using Microsoft.TeamFoundation.Client;
using Microsoft.TeamFoundation.WorkItemTracking.Client;
...
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  TfsTeamProjectCollection tfs =
        TfsTeamProjectCollectionFactory
            .GetTeamProjectCollection(new Uri(serverUri));
  WorkItemStore workItemStore = new WorkItemStore(tfs);
  WorkItem item = workItemStore.GetWorkItem(workItemId);
  item.Open();
  item.Title = "something";
  item.Save();
} 
```

## <a name="accessing-the-work-item-reference-links"></a>Acessando os links de referência do item de trabalho
 Você pode acessar os links da seguinte maneira:

```
//Get:
string linkString = element.GetReference(ReferenceConstants.WorkItem);
// Set:
element.AddReference(ReferenceConstants.WorkItem, linkString, true);

```

 O formato de `linkString` é:

 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`

 em que:

- O URI para o servidor seria:

   `http://tfServer:8080/tfs/projectCollection`

   O caso é importante `projectCollection`no.

- `RepositoryGuid`pode ser obtido de sua conexão do TFS:

  ```csharp
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;
  RepositoryGuid= tpc.InstanceId;

  ```

  Para obter mais informações sobre referências, consulte [anexar cadeias de caracteres de referência a elementos de modelo UML](../modeling/attach-reference-strings-to-uml-model-elements.md).

## <a name="see-also"></a>Consulte também

- [Microsoft. TeamFoundation. WorkItemTracking. Client. WorkItemStore](/previous-versions/visualstudio/visual-studio-2013/bb179850(v=vs.120))
- [Vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md)
- [Anexar cadeias de caracteres de referência a elementos de modelo UML](../modeling/attach-reference-strings-to-uml-model-elements.md)
- [Definir e instalar uma extensão de modelagem](../modeling/define-and-install-a-modeling-extension.md)
- [Programando com a API UML](../modeling/programming-with-the-uml-api.md)
