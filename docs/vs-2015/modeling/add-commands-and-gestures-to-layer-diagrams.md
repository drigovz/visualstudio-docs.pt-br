---
title: Adicionar comandos e gestos aos diagramas de camada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7b0c54975cdd5bc86f77dddbd5ca1a56c1896394
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655313"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Adicionar comandos e gestos a diagramas de camada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode definir comandos de menu de contexto e manipuladores de gestos em diagramas de camadas no Visual Studio. Você pode empacotar essas extensões em uma extensão de integração do Visual Studio (VSIX) que pode ser distribuída para outros usuários do Visual Studio.

 Você pode definir vários manipuladores de comando e de gesto no mesmo projeto do Visual Studio, se desejar. Você também pode combinar vários desses projetos em um VSIX. Por exemplo, você pode definir um único VSIX que inclui comandos de camada, uma linguagem específica de domínio e comandos para diagramas UML.

> [!NOTE]
> Você também pode personalizar a validação de arquitetura, na qual o código-fonte dos usuários é comparado com os diagramas de camada. Você deve definir a validação de arquitetura em um projeto do Visual Studio separado. Você pode adicioná-lo ao mesmo VSIX que outras extensões. Para obter mais informações, consulte [Adicionar validação de arquitetura personalizada a diagramas de camada](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Requisitos
 Consulte [requisitos](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definindo um comando ou gesto em um novo VSIX
 O método mais rápido de criar uma extensão é usar o modelo de projeto. Isso coloca o código e o manifesto do VSIX no mesmo projeto.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Para definir uma extensão usando um modelo de projeto

1. Crie um projeto em uma nova solução, usando o comando **novo projeto** no menu **arquivo** .

2. Na caixa de diálogo **novo projeto** , em **modelagem de projetos**, selecione extensão de **comando de designer de camada** ou extensão de gesto de designer de **camada**.

    O modelo cria um projeto que contém um pequeno exemplo de trabalho.

3. Para testar a extensão, pressione **Ctrl + F5** ou **F5**.

    Uma instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é iniciada. Nessa instância, crie um diagrama de camada. O comando ou a extensão do gesto deve funcionar neste diagrama.

4. Feche a instância experimental e modifique o código de exemplo. Para obter mais informações, consulte [navegar e atualizar modelos de camada no código do programa](../modeling/navigate-and-update-layer-models-in-program-code.md).

5. Você pode adicionar mais manipuladores de comando ou de gesto ao mesmo projeto. Saiba mais em uma das seções a seguir:

    [Definindo um comando de menu](#command)

    [Definindo um manipulador de gestos](#gesture)

6. Para instalar a extensão na instância principal do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ou em outro computador, localize o arquivo **. vsix** no *bin \\ *. Copie-o para o computador em que você deseja instalá-lo e clique duas vezes nele. Para desinstalá-lo, use **extensões e atualizações** no menu **ferramentas** .

## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Adicionando um comando ou gesto para um VSIX separado
 Se você quiser criar um VSIX que contém comandos, validadores de camada e outras extensões, recomendamos que você crie um projeto para definir o VSIX e separe projetos para os manipuladores. Para obter informações sobre outros tipos de extensão de modelagem, consulte [estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Para adicionar extensões de camada a um VSIX separado

1. Crie um projeto de biblioteca de classes em uma solução nova ou existente do Visual Studio. Na caixa de diálogo **novo projeto** , clique em **Visual C#** e, em seguida, clique em **biblioteca de classes**. Este projeto conterá classes de manipulador de comando ou de gesto.

    > [!NOTE]
    > Você pode definir mais de uma classe de manipulador de comando ou de gesto em uma biblioteca de classes, mas deve definir classes de validação de camada em uma biblioteca de classes separada.

2. Identifique ou crie um projeto VSIX em sua solução. Um projeto VSIX contém um arquivo chamado **Source. Extension. vsixmanifest**. Para adicionar um projeto VSIX:

    1. Na caixa de diálogo **novo projeto** , expanda **Visual C#**, clique em **extensibilidade**e, em seguida, clique em **projeto VSIX**.

    2. Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto VSIX e clique em **definir como projeto de inicialização**.

    3. Clique em **selecionar edições** e verifique se o **Visual Studio** está marcado.

3. Em **Source. Extension. vsixmanifest**, em **ativos**, adicione o comando ou o projeto de manipulador de gestos como um componente MEF.

    1. Na guia **ativos**., escolha **novo**.

    2. Em **tipo**, selecione **Microsoft. VisualStudio. MefComponent**.

    3. Na **origem**, selecione **projeto na solução atual** e selecione o nome do seu projeto de manipulador de comando ou de gesto.

    4. Salve o arquivo.

4. Retorne ao projeto de manipulador de comando ou de gesto e adicione as referências de projeto a seguir.

|**Referência**|**O que isso permite que você faça**|
|-------------------|------------------------------------|
|Arquivos de Programas\microsoft Visual Studio [versão] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Criar e editar camadas|
|Microsoft. VisualStudio. Uml. interfaces|Criar e editar camadas|
|Microsoft. VisualStudio. ArchitectureTools. Extensibility|Modificar formas em diagramas|
|System. ComponentModel. composição|Definir componentes usando Managed Extensibility Framework (MEF)|
|Microsoft. VisualStudio. Modeling. Sdk. versão|Definir extensões de modelagem|
|Microsoft. VisualStudio. Modeling. Sdk. Diagrams. versão|Atualizar formas e diagramas|

1. Edite o arquivo de classe no projeto de biblioteca de classes C# para conter o código para sua extensão. Saiba mais em uma das seções a seguir:

     [Definindo um comando de menu](#command)

     [Definindo um manipulador de gestos](#gesture)

     Consulte também [navegar e atualizar modelos de camada no código do programa](../modeling/navigate-and-update-layer-models-in-program-code.md).

2. Para testar o recurso, pressione CTRL + F5 ou F5. Uma instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é aberta. Nesta instância, crie ou abra um diagrama de camada.

3. Para instalar o VSIX na instância principal do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ou em outro computador, localize o arquivo **. vsix** no diretório **bin** do projeto VSIX. Copie-o para o computador em que você deseja instalar o VSIX. Clique duas vezes no arquivo VSIX no Windows Explorer (explorador de arquivos no Windows 8).

     Para desinstalá-lo, use **extensões e atualizações** no menu **ferramentas** .

## <a name="defining-a-menu-command"></a><a name="command"></a> Definindo um comando de menu
 Você pode adicionar mais definições de comando de menu a um gesto ou projeto de comando existente. Cada comando é definido por uma classe que tem as seguintes características:

- A classe é declarada da seguinte maneira:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- O namespace e o nome da classe não são importantes.

- Os métodos que implementam `ICommandExtension` são os seguintes:

  - `string Text {get;}` -O rótulo que aparece no menu.

  - `void QueryStatus(IMenuCommand command)` -chamado quando o usuário clica com o botão direito do mouse no diagrama e determina se o comando deve ser visível e habilitado para a seleção atual do usuário.

  - `void Execute(IMenuCommand command)` -chamado quando o usuário seleciona o comando.

- Para determinar a seleção atual, você pode importar `IDiagramContext` :

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

  Para obter mais informações, consulte [navegar e atualizar modelos de camada no código do programa](../modeling/navigate-and-update-layer-models-in-program-code.md).

  Para adicionar um novo comando, crie um novo arquivo de código que contenha o exemplo a seguir. Em seguida, teste e edite-o.

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for Layer diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Definindo um manipulador de gestos
 Um manipulador de gestos responde quando o usuário arrasta itens para o diagrama de camada e quando o usuário clica duas vezes em qualquer lugar no diagrama.

 Para o projeto VSIX do manipulador de gestos ou comando existente, você pode adicionar um arquivo de código que define um manipulador de gestos:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;
namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

 Observe os seguintes pontos sobre manipuladores de gestos:

- Os membros do `IGestureExtension` são os seguintes:

   **OnDoubleClick** – chamado quando o usuário clica duas vezes em qualquer lugar do diagrama.

   **CanDragDrop** -chamado repetidamente à medida que o usuário move o mouse enquanto arrasta um item para o diagrama. Ele deve funcionar rapidamente.

   **OnDragDrop** – chamado quando o usuário remove um item no diagrama.

- O primeiro argumento para cada método é um `IShape` , a partir do qual você pode obter o elemento de camada. Por exemplo:

  ```
  public void OnDragDrop(IShape target, IDataObject data)
  {
      ILayerElement element = target.GetLayerElement();
      if (element is ILayer)
      {
          // ...
      }
  }
  ```

- Os manipuladores para alguns tipos de itens arrastados já estão definidos. Por exemplo, o usuário pode arrastar itens de Gerenciador de Soluções para um diagrama de camada. Você não pode definir um manipulador de arrastar para esses tipos de item. Nesses casos, seus `DragDrop` métodos não serão invocados.

  Para obter mais informações sobre como decodificar outros itens quando eles são arrastados para o diagrama, consulte [definir um manipulador de gestos em um diagrama de modelagem](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="see-also"></a>Consulte Também
 [Navegue e atualize os modelos de camada no código do programa](../modeling/navigate-and-update-layer-models-in-program-code.md) [Adicionar validação de arquitetura personalizada a diagramas de camada](../modeling/add-custom-architecture-validation-to-layer-diagrams.md) [definir e instalar uma extensão de modelagem](../modeling/define-and-install-a-modeling-extension.md)
