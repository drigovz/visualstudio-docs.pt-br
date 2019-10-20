---
title: Adicionar propriedades personalizadas a diagramas de camada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec1c7c94c8a0e6aa233cf21f9b57e093cc430d48
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655294"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Adicionar propriedades personalizadas a diagramas de camada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao escrever o código de extensão para diagramas de camada, você pode armazenar valores com qualquer elemento em um diagrama de camada. Os valores serão persistidos quando o diagrama for salvo e aberto novamente. Você também pode ter essas propriedades exibidas na janela **Propriedades** para que os usuários possam vê-las e editá-las. Por exemplo, você pode permitir que os usuários especifiquem uma expressão regular para cada camada e escrevam o código de validação para verificar se os nomes das classes em cada camada estão em conformidade com o padrão especificado pelo usuário.

## <a name="properties-not-visible-to-the-user"></a>Propriedades não visíveis para o usuário
 Se você quiser apenas que seu código anexe valores a qualquer elemento em um diagrama de camada, não precisará definir um componente MEF. Há um dicionário chamado `Properties` em [ILayerElement](/previous-versions/ff644511(v=vs.140)). Basta adicionar valores de marshaling ao dicionário de qualquer elemento de camada. Eles serão salvos como parte do diagrama de camadas. Para obter mais informações, consulte [navegar e atualizar modelos de camada no código do programa](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="properties-that-the-user-can-edit"></a>Propriedades que o usuário pode editar
 **Preparação inicial**

> [!IMPORTANT]
> Para exibir as propriedades, você deve fazer a seguinte alteração em cada computador em que deseja que as propriedades da camada fiquem visíveis.
>
>  1. Execute o bloco de notas usando **Executar como administrador**. Abrir `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`
>
>  2. Dentro do elemento `Content`, adicione:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
>  3. Na seção **Ferramentas do Visual Studio** do menu Iniciar do aplicativo do Visual Studio, abra **prompt de comando do desenvolvedor**.
>
>     Digita
>
>     `devenv /rootSuffix /updateConfiguration`
>
>     `devenv /rootSuffix Exp /updateConfiguration`
>
>  4. Reinicie o Visual Studio.

 **Verifique se o código está em um projeto VSIX**

 Se sua propriedade fizer parte de um comando, um gesto ou um projeto de validação, você não precisará adicionar nada. O código para sua propriedade personalizada deve ser definido em um projeto de extensibilidade do Visual Studio definido como um componente MEF. Para obter mais informações, consulte [adicionar comandos e gestos a diagramas de camada](../modeling/add-commands-and-gestures-to-layer-diagrams.md) ou [Adicionar validação de arquitetura personalizada a diagramas de camada](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 **Definir a propriedade personalizada**

 Para criar uma propriedade personalizada, defina uma classe como esta:

```
[Export(typeof(IPropertyExtension))]
public class MyProperty
      : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

 Você pode definir propriedades em [ILayerElement](/previous-versions/ff644511(v=vs.140)) ou em qualquer uma de suas classes derivadas, que incluem:

- `ILayerModel`-o modelo

- `ILayer`-cada camada

- `ILayerDependencyLink`-os links entre camadas

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Exemplo
 O código a seguir é um descritor de propriedade personalizada típico. Ele define uma propriedade booliana no modelo de camada (`ILayerModel`) que permite que o usuário forneça valores para um método de validação personalizado.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Consulte também
 [Estender diagramas de camada](../modeling/extend-layer-diagrams.md)
