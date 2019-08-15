---
title: Migração de extensibilidade Designer XAML
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 6ffa8888529586e23d6f9762c3ec5b724c708ca5
ms.sourcegitcommit: ab2c49ce72ccf44b27b5c8852466d15a910453a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69024550"
---
# <a name="xaml-designer-extensibility-migration"></a>Migração de extensibilidade do designer XAML

No Visual Studio 2019, o designer XAML dá suporte a duas arquiteturas diferentes: a arquitetura de isolamento de designer e a arquitetura de isolamento de superfície mais recente. Essa transição de arquitetura é necessária para dar suporte a tempos de execução de destino que não podem ser hospedados em um processo de .NET Framework. A mudança para a arquitetura de isolamento da superfície introduz alterações significativas no modelo de extensibilidade de terceiros. Este artigo descreve essas alterações, que estão disponíveis no Visual Studio 2019 a partir da versão 16,3.

O **isolamento de designer** é usado pelo designer do WPF para projetos direcionados ao .NET Framework e oferece suporte a extensões *. Design. dll* . O código do usuário, as bibliotecas de controle e as extensões de terceiros são carregados em um processo externo (*XDesProc. exe*) junto com o código do designer e os painéis de designer reais.

O **isolamento de superfície** é usado pelo designer do UWP. Ele também é usado pelo designer do WPF para projetos direcionados ao .NET Core. No isolamento de superfície, somente as bibliotecas de código e controle do usuário são carregadas em um processo separado, enquanto o designer e seus painéis são carregados no processo do Visual Studio (*devenv. exe*). O tempo de execução usado para executar as bibliotecas de código e controle do usuário é diferente daquele usado pelo .NET Framework para o designer real e o código de extensibilidade de terceiros.

![extensibilidade-migração-arquitetura](media/xaml-designer-extensibility-migration-architecture.png)

Devido a essa transição de arquitetura, as extensões de terceiros não são mais carregadas no mesmo processo que as bibliotecas de controle de terceiros. As extensões não podem mais ter dependências diretas em bibliotecas de controle ou acessar diretamente os objetos de tempo de execução. As extensões que foram escritas anteriormente para a arquitetura de isolamento do designer usando a API *Microsoft. Windows. Extensibility. dll* devem ser migradas para uma nova abordagem para trabalhar com a arquitetura de isolamento da superfície. Na prática, uma extensão existente precisará ser compilada em relação aos novos assemblies da API de extensibilidade. O acesso a tipos de controle em tempo de execução via instâncias [typeof](/dotnet/csharp/language-reference/keywords/typeof) ou runtime deve ser substituído ou removido porque as bibliotecas de controle agora estão carregadas em um processo diferente.

## <a name="new-extensibility-api-assemblies"></a>Novos assemblies de API de extensibilidade

Os novos assemblies da API de extensibilidade são semelhantes aos assemblies da API de extensibilidade existentes, mas seguem um esquema de nomenclatura diferente para diferenciá-los. Da mesma forma, os nomes de namespace foram alterados para refletir os novos nomes de assembly.

| Assembly de API de isolamento de designer            | Assembly de API de isolamento de superfície                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Nova extensão de arquivo e descoberta

Em vez de usar a extensão de arquivo *. Design. dll* , novas extensões de superfície serão descobertas usando a extensão de arquivo *. designtools. dll* . *. as extensões. Design. dll* e *. designtools. dll* podem existir na mesma subpasta de *design* .

Enquanto as bibliotecas de controle de terceiros são compiladas para o tempo de execução de destino real (.NET Core ou UWP), a extensão *. designtools. dll* sempre deve ser compilada como um assembly .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Desacoplar tabelas de atributos de tipos de tempo de execução

O modelo de extensibilidade de isolamento de superfície não permite que as extensões dependam de bibliotecas de controle reais e, portanto, as extensões não podem referenciar tipos da biblioteca de controle. Por exemplo, *MyLibrary. designtools. dll* não deve ter uma dependência em *MyLibrary. dll*.

Essas dependências eram mais comuns ao registrar metadados para tipos por meio de tabelas de atributos. O código de extensão que referencia tipos de biblioteca de controle diretamente por meio de [typeof](/dotnet/csharp/language-reference/keywords/typeof) ou [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) é substituído nas novas APIs usando nomes de tipo com base em cadeia de caracteres:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Provedores de recursos e API de modelo

Os provedores de recursos são implementados em assemblies de extensão e carregados no processo do Visual Studio. `FeatureAttribute`o continuará a referenciar tipos de provedor de recursos diretamente usando [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Atualmente, há suporte para os seguintes provedores de recursos:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`

Como os provedores de recursos agora são carregados em um processo diferente do código de tempo de execução real e das bibliotecas de controle, eles não podem mais acessar objetos de tempo de execução diretamente. Em vez disso, todas essas interações devem ser convertidas para usar as APIs baseadas em modelo correspondentes. A API de modelo foi atualizada e o acesso a <xref:System.Type> ou <xref:System.Object> não está mais disponível ou foi substituído por `TypeIdentifier` e `TypeDefinition`.

`TypeIdentifier`representa uma cadeia de caracteres sem um nome de assembly que identifica um tipo. Um `TypeIdenfifier` pode ser resolvido para um `TypeDefinition` para consultar informações adicionais sobre o tipo. `TypeDefinition`as instâncias não podem ser armazenadas em cache no código de extensão.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

APIs removidas do conjunto de APIs de extensibilidade de isolamento de superfície:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

APIs que usam `TypeIdentifier` em vez <xref:System.Type>de:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

As APIs que `TypeIdentifier` usam em <xref:System.Type> vez de e não oferecem mais suporte a argumentos de construtor:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

APIs que usam `TypeDefinition` em vez <xref:System.Type>de:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`

APIs que usam `ModelItem` em vez <xref:System.Object>de:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Além disso `ModelItem` , APIs `SetValue` como o oferecerão suporte apenas a instâncias de tipos primitivos ou tipos de .NET Framework internos que podem ser convertidos para o tempo de execução de destino. Atualmente, há suporte para esses tipos:

* Tipos de .NET Framework primitivos `Byte`: `Char` `Boolean`, `DateTime`, `Double` `Enum` ,,`Guid`,,, ,`Int64`, ,`SByte` , `Int16` `Int32` `Nullable` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* Tipos de .NET Framework do WPF conhecidos (e tipos derivados `Brush`) `Color`: `CompositeTransform`, `CornerRadius`, `Duration`, `EasingFunctionBase` `EasingMode`,, `EllipseGeometry`, `FontFamily`, `GeneralTransform`, `Geometry` ,, , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Por exemplo:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

Mais exemplos de código estão disponíveis no repositório [XAML-designer-Extensibility-Samples](https://github.com/microsoft/xaml-designer-extensibility-samples) .

## <a name="limited-support-for-designdll-extensions"></a>Suporte limitado para extensões. Design. dll

Se qualquer extensão *. designtools. dll* for descoberta para uma biblioteca de controle, ela será carregada primeiro e a descoberta para as extensões *. Design. dll* será ignorada.

Se não houver extensões *. designtools. dll* presentes, mas uma extensão *. Design. dll* for encontrada, o serviço XAML Language tentará carregar esse assembly para extrair as informações da tabela de atributos para dar suporte a cenários básicos de editor e de Inspetor de propriedades. Esse mecanismo é limitado no escopo. Ele não permite o carregamento de extensões de isolamento de designer para executar provedores de recursos, mas pode fornecer suporte básico para bibliotecas de controle do WPF existentes.
