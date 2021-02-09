---
title: Atualizando formas e conectores para refletir o modelo
description: Saiba que, em uma linguagem específica de domínio no Visual Studio, você pode fazer com que a aparência de uma forma reflita o estado do modelo subjacente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 57f3785fe232b20123475bd85be2be7148e5b87e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924348"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Atualizar formas e conectores para refletir o modelo

Em uma linguagem específica de domínio no Visual Studio, você pode fazer com que a aparência de uma forma reflita o estado do modelo subjacente.

Os exemplos de código neste tópico devem ser adicionados a um `.cs` arquivo em seu `Dsl` projeto. Você precisa dessas diretivas em cada arquivo:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Definir propriedades de mapa de formas para controlar a visibilidade de um decorador

Você pode controlar a visibilidade de um decorador sem escrever o código do programa, configurando o mapeamento entre a forma e a classe de domínio na definição de DSL. Para obter mais informações, consulte [como definir um idioma de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Expor a cor e o estilo de uma forma como propriedades

Na definição de DSL, clique com o botão direito do mouse na classe Shape, aponte para **Adicionar exposto** e clique em um dos itens como **cor de preenchimento**.

A forma agora tem uma propriedade Domain que pode ser definida no código do programa ou como um usuário. Por exemplo, para defini-lo no código do programa de um comando ou regra, você poderia escrever:

`shape.FillColor = System.Drawing.Color.Red;`

Se você quiser tornar a variável de propriedade somente sob o controle do programa, e não pelo usuário, selecione a nova propriedade de domínio, como **cor de preenchimento** no diagrama de definição de DSL. Em seguida, na janela Propriedades, Set **é navegável** para `false` ou definido **é a interface do usuário ReadOnly** para `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definir regras de alteração para tornar a cor, o estilo ou o local depende das propriedades do elemento de modelo
 Você pode definir regras que atualizam a aparência da forma dependente de outras partes do modelo. Por exemplo, você pode definir uma regra de alteração em um elemento de modelo que atualiza a cor de sua forma dependente das propriedades do elemento de modelo. Para obter mais informações sobre regras de alteração, consulte [regras propagar alterações no modelo](../modeling/rules-propagate-changes-within-the-model.md).

 Você deve usar regras somente para atualizar as propriedades mantidas no repositório, pois as regras não são invocadas quando o comando desfazer é executado. Isso não inclui alguns recursos gráficos, como o tamanho e a visibilidade de uma forma. Para atualizar esses recursos de uma forma, consulte [atualizando recursos gráficos que não são de armazenamento](#OnAssociatedProperty).

 O exemplo a seguir pressupõe que você tenha exposto `FillColor` como uma propriedade de domínio, conforme descrito na seção anterior.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Usar OnChildConfigured para inicializar as propriedades de uma forma

Para definir as propriedades de uma forma quando ela é criada pela primeira vez, a substituição `OnChildConfigured()` em uma definição parcial da classe de diagrama. A classe de diagrama é especificada em sua definição de DSL e o código gerado está em **Dsl\Generated Code\Diagram.cs**. Por exemplo:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

Esse método pode ser usado para propriedades de domínio e recursos que não são de armazenamento, como o tamanho da forma.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Usar AssociateValueWith () para atualizar outros recursos de uma forma

Para alguns recursos de uma forma, como se ele tem uma sombra ou o estilo de seta de um conector, não há um método interno de expor o recurso como uma propriedade de domínio.  As alterações em tais recursos não estão sob o controle do sistema de transação. Portanto, não é apropriado atualizá-los usando regras, pois as regras não são invocadas quando o usuário executa o comando desfazer.

Em vez disso, você pode atualizar esses recursos usando o <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . No exemplo a seguir, o estilo de seta de um conector é controlado por um valor de uma propriedade de domínio na relação que o conector exibe:

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` deve ser chamado uma vez para cada propriedade de domínio que você deseja registrar. Depois de ser chamado, qualquer alteração na propriedade especificada chamará todas as `OnAssociatedPropertyChanged()` formas que apresentam o elemento de modelo da propriedade.

Não é necessário chamar `AssociateValueWith()` para cada instância. Embora InitializeResources seja um método de instância, ele é invocado apenas uma vez para cada classe Shape.
