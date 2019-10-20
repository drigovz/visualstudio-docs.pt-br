---
title: Navegar no modelo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7b90d8b532b004a7cbdaeed762300a0daf9ab45c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668538"
---
# <a name="navigate-the-uml-model"></a>Navegar no modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico apresenta os tipos principais do modelo UML.

## <a name="the-model-elements-model-and-model-store"></a>Os elementos do modelo, o modelo e o repositório de modelos
 Os tipos definidos no assembly **Microsoft. VisualStudio. Uml. interfaces. dll** correspondem aos tipos definidos na [especificação UML, versão 2.1.2](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).

 Os tipos na especificação UML são percebidos como interfaces no Visual Studio. A letra ' I ' é precedida ao nome de cada tipo. Por exemplo: [ielemento](/previous-versions/dd516035(v=vs.140)), [IClass](/previous-versions/dd523539%28v%3dvs.140%29), [IOperation](/previous-versions/dd481186(v=vs.140)).

 Todos os tipos, exceto ielemento, herdam Propriedades de um ou mais supertipos.

- Para obter um resumo dos tipos de modelo, consulte [tipos de elementos de modelo UML](../modeling/uml-model-element-types.md).

- Para obter detalhes completos da API, consulte [referência de API para extensibilidade de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

### <a name="relationships"></a>Relações
 As propriedades e relações definidas na especificação UML são implementadas como propriedades do .NET.

 A maioria das relações é navegável em ambas as direções. Uma relação corresponde a um par de propriedades, com uma propriedade no tipo em cada extremidade. Por exemplo, as propriedades `IElement.Owner` e `IElement.OwnedElements` representam duas extremidades de uma relação. Portanto, essa expressão sempre será avaliada como true:

 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`

 Muitas relações, como IAssociation, também são representadas por um objeto que pode ter suas próprias propriedades.

 Se você excluir um elemento do modelo, qualquer relação na qual ele faz parte será excluída automaticamente e a propriedade na outra extremidade será atualizada.

 Se a especificação UML atribuir uma multiplicidade de 0.. 1 a uma propriedade, ela poderá ter o valor `null`. Uma multiplicidade com um máximo maior que 1 significa que a propriedade .NET tem*o tipo de `IEnumerable<` Type* : `>`.

 Para obter mais informações sobre como percorrer relações, consulte [navegar em relações com a API UML](../modeling/navigate-relationships-with-the-uml-api.md).

### <a name="the-ownership-tree"></a>A árvore de propriedade
 Um modelo contém uma árvore de objetos [ielemento](/previous-versions/dd516035(v=vs.140)) . Cada elemento tem propriedades `OwnedElements` e `Owner`.

 Na maioria dos casos, os destinos das propriedades `Owner` e `OwnedElements` também são referenciados por outras propriedades que têm nomes mais específicos. Por exemplo, cada operação de UML pertence a uma classe UML. Portanto, [IOperation](/previous-versions/dd481186(v=vs.140)) tem uma propriedade chamada [IOperation. Class](/previous-versions/dd473473%28v%3dvs.140%29)e, em cada objeto [IOperation](/previous-versions/dd481186(v=vs.140)) , `Class == Owner`.

 O elemento superior da árvore, que não tem proprietário, é um `AuxiliaryConstructs.IModel`. O IModel está contido em um `IModelStore`, no qual é o [IModelStore. root](/previous-versions/ee789368(v=vs.140)).

 Cada elemento de modelo é criado com um proprietário. Para obter mais informações, consulte [criar elementos e relações em modelos UML](../modeling/create-elements-and-relationships-in-uml-models.md).

 ![Diagrama de classe: modelo, diagrama, forma e elemento](../modeling/media/uml-mm1.png)

## <a name="shapes-and-diagrams"></a>Formas e diagramas
 Elementos no modelo UML podem ser exibidos em diagramas. Tipos diferentes de diagramas podem exibir subtipos diferentes de ielemento.

 Em alguns casos, um elemento pode aparecer em mais de um diagrama. Por exemplo, um elemento IUseCase pode ter vários IShapes, que podem aparecer em um diagrama ou em diagramas diferentes.

 As formas são organizadas em uma árvore. As bordas da árvore são representadas pelas propriedades ParentShape e ChildShapes. Os diagramas são as únicas formas que não têm pais. As formas na superfície de um diagrama são compostas por partes menores. Por exemplo, uma forma de classe tem compartimentos para atributos e operações.

 Para obter mais informações sobre formas, consulte [exibir um modelo UML em diagramas](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="access-to-the-model-in-extensions"></a>Acesso ao modelo em extensões
 Em extensões de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] definidas como componentes do MEF, você pode declarar propriedades que importam informações do contexto no qual a extensão é executada.

|Tipo de atributo|O que fornece acesso a|Mais informações|
|--------------------|----------------------------------|----------------------|
|Microsoft. VisualStudio. ArchitectureTools. Extensibility. Presentation<br /><br /> . IDiagramContext<br /><br /> (em Microsoft. VisualStudio. ArchitectureTools. Extensibility. dll)|O diagrama de foco atual.|[Definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|
|Microsoft. VisualStudio. Modeling. ExtensionEnablement<br /><br /> . ILinkedUndoContext<br /><br /> (em Microsoft. VisualStudio. Modeling. Sdk. [versão]. dll)|Permite agrupar alterações em transações.|[Vincular atualizações de modelo UML usando transações](../modeling/link-uml-model-updates-by-using-transactions.md)|
|Microsoft. VisualStudio. Shell. SVsServiceProvider<br /><br /> (em Microsoft. VisualStudio. Shell. imutável. [versão]. dll)|O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do host. A partir daí, você pode acessar arquivos, projetos e outros aspectos.|[Abrir um modelo UML usando a API do Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|

### <a name="to-get-the-context"></a>Para obter o contexto
 Declare uma ou ambas as seguintes interfaces dentro de sua classe de extensão:

```
[Import] public IDiagramContext DiagramContext { get; set; }

```

 O Managed Extensibility Framework (MEF) os associará a definições das quais você pode obter o diagrama atual, o repositório de modelos, o objeto raiz e assim por diante:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
IClassDiagram classDiagram = diagram as IClassDiagram;
       // or diagrams of other types
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

### <a name="to-get-the-current-selection"></a>Para obter a seleção atual

```
// All selected shapes and their elements
foreach (IShape shape in diagram.SelectedShapes)
{
   IDiagram selectedDiagram = shape as IDiagram;
   if (selectedDiagram != null)
   { // no shape selected - user right-clicked the diagram
     ... Context.CurrentDiagram ...
   }
   else
   {
     IElement selectedElement = shape.Element;
   ...}
// All selected shapes that display a specfic type of element
foreach (IShape<IInterface> in
   diagram.GetSelectedShapes<IInterface>())
{...}
```

## <a name="accessing-another-model-or-diagrams"></a>Acessando outro modelo ou diagramas
 Você pode:

- Use [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] barramento de modelo para criar links entre elementos em modelos diferentes. Para obter mais informações, consulte [integrar modelos UML com outros modelos e ferramentas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Carregue um projeto de modelagem e diagramas no modo somente leitura sem torná-lo visível na interface do usuário [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obter mais informações, consulte [ler um modelo UML no código do programa](../modeling/read-a-uml-model-in-program-code.md).

- Abra um projeto de modelagem e seus diagramas em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e, em seguida, acesse o conteúdo. Para obter mais informações, consulte [abrir um modelo UML usando a API do Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="see-also"></a>Consulte também

- [Estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
- [Programando com a API UML](../modeling/programming-with-the-uml-api.md)
