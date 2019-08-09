---
title: Navegar e atualizar modelos de camada no código do programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb0c600830c114ca24f9cdc0619fd84c6e18d232
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871820"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Navegar e atualizar modelos de camada no código do programa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico descreve os elementos e as relações em modelos de camada, que você pode navegar e atualizar usando o código do programa. Para obter mais informações sobre diagramas de camada do ponto de vista do usuário [, consulte Diagramas de camada: Diagramas [de referência](../modeling/layer-diagrams-reference.md) e de camada: Diretrizes](../modeling/layer-diagrams-guidelines.md).

 O modelo `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` descrito neste tópico é uma fachada em um modelo <xref:Microsoft.VisualStudio.GraphModel> mais geral. Se você estiver escrevendo um [comando de menu ou uma extensão](../modeling/add-commands-and-gestures-to-layer-diagrams.md)de gesto `Layer` , use o modelo. Se você estiver escrevendo uma [extensão de validação de camada](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), será mais fácil usar `GraphModel`o.

## <a name="transactions"></a>Transações
 Ao atualizar um modelo, considere incluir as alterações em uma `ILinkedUndoTransaction`. Esse procedimento agrupará as alterações em uma transação. Se qualquer uma das alterações falhar, toda a transação será revertida. Se o usuário desfizer uma alteração, todas as alterações serão desfeitas em conjunto.

 Para obter mais informações, consulte [vincular atualizações de modelo UML usando transações](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Confinamento
 ![ILayer e ILayerModel podem conter ILayers.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Camadas ([ILayer](/previous-versions/ff644251(v=vs.140))) e o modelo de camada ([ILayerModel](/previous-versions/ff643069(v=vs.140))) podem conter comentários e camadas.

 Uma camada (`ILayer`) pode estar contida em um modelo de camada (`ILayerModel`) ou pode ser aninhada em outra `ILayer`.

 Para criar um comentário ou uma camada, use os métodos de criação no contêiner apropriado.

## <a name="dependency-links"></a>Vínculos de dependência
 Um vínculo de dependência é representado por um objeto. Ele pode ser navegado em qualquer direção:

 ![Um ILayerDependencyLink conecta dois ILayers.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Para criar um vínculo de dependência, chame `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Comentários
 Os comentários podem ser encontrados dentro de camadas ou do modelo de camada e também podem ser vinculados a qualquer elemento de camada:

 ![Os comentários podem ser anexados a qualquer elemento de camada.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Um comentário pode ser vinculado a qualquer número de elementos, incluindo zero.

 Para obter os comentários anexados a um elemento de camada, use:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> A propriedade `Comments` de uma `ILayer` recebe comentários que estão contidos na `ILayer`. Não recebe os comentários vinculados a ela.

 Crie um comentário, invocando `CreateComment()` no contêiner adequado.

 Crie um link usando `CreateLink()` no comentário.

## <a name="layer-elements"></a>Elementos de camada
 Todos os tipos de elementos que podem estar contidos em um modelo são elementos de camada:

 O ![conteúdo do diagrama de camadas é ILayerElements.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Propriedades
 Cada `ILayerElement` tem um dicionário de cadeia chamado `Properties`. Você pode usar este dicionário para anexar informações arbitrárias a qualquer elemento da camada.

## <a name="artifact-references"></a>Referências de artefato
 Uma referência de artefato ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))) representa o vínculo entre uma camada e um item de projeto, como um arquivo, uma classe ou uma pasta. O usuário cria artefatos quando cria uma camada ou adiciona a ele arrastando itens de Gerenciador de Soluções, Modo de Exibição de Classe ou pesquisador de objetos em um diagrama de camada. Qualquer número de referências de artefato pode ser vinculado a uma camada.

 Cada linha do Gerenciador de Camadas exibe uma referência de artefato. Para obter mais informações, consulte [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md).

 Os principais tipos e métodos relacionados a referências de artefato são os seguintes:

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140)). A propriedade Categorias indica que tipo de artefato é referenciado, tal como uma classe, arquivo executável ou assembly. As categorias determinam como o Identificador identifica o artefato de destino.

 [ArtifactReferenceExtensions. CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) cria uma referência de artefato de <xref:EnvDTE.Project> um <xref:EnvDTE.ProjectItem>ou. Esta é uma operação assíncrona. Portanto, você geralmente fornece um retorno de chamada realizado quando a criação é concluída.

 As referências de artefato de camada não devem ser confundidas com artefatos em diagramas de casos de uso.

## <a name="shapes-and-diagrams"></a>Formas e diagramas
 Dois objetos são usados para representar cada elemento em um modelo de camada: `ILayerElement`um e um [IShape](/previous-versions/ee806673(v=vs.140)). O `IShape` representa a posição e o tamanho da forma no diagrama. Nos modelos de camadas, cada `ILayerElement` tem um `IShape` e cada `IShape` em um diagrama de camada tem um `ILayerElement`. `IShape` também é usado para modelos UML. Portanto, nem todo `IShape` tem um elemento de camada.

 Da mesma maneira, o `ILayerModel` é exibido em um [IDiagram](/previous-versions/ee789658(v=vs.140)).

 No código de um comando personalizado ou manipulador de gestos, você pode obter o diagrama atual e a seleção atual de formas da importação do `DiagramContext`:

```
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

 ![Cada ILayerElement é apresentado por um IShape.](../modeling/media/layerapi-shapes.png)

 [IShape](/previous-versions/ee806673(v=vs.140)) e [IDiagram](/previous-versions/ee789658(v=vs.140)) também são usados para exibir modelos UML. Para obter mais informações, consulte [exibir um modelo UML em diagramas](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>Consulte também

- [Adicionar comandos e gestos a diagramas de camada](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Adicionar validação de arquitetura personalizada a diagramas de camada](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Adicionar propriedades personalizadas a diagramas de camada](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagramas de camada: referência](../modeling/layer-diagrams-reference.md)
- [Diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md)
- [Estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
