---
title: Migração de extensibilidade do Designer XAML
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 4485e9a11cb4770477374deed651fbff2df6df52
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890325"
---
# <a name="xaml-designer-extensibility-migration"></a>Migração de extensibilidade do designer XAML

No Visual Studio de 2019, o designer XAML dá suporte a duas arquiteturas diferentes: a arquitetura de designer de isolamento e a arquitetura de superfície de isolamento mais recente. Essa transição de arquitetura é necessário para dar suporte a tempos de execução de destino que não podem ser hospedados em um processo do .NET Framework. Mover para a arquitetura de isolamento de superfície introduz mudanças significativas para o modelo de extensibilidade de terceiros. Este artigo descreve essas alterações que estão disponíveis no canal de visualização 16.2 de 2019 do Visual Studio.

**Isolamento de Designer** é usado pelo designer do WPF para projetos destinados ao .NET Framework e dá suporte a *. dll* extensões. Código do usuário, bibliotecas de controle e extensões de terceiros são carregadas em um processo externo (*XDesProc.exe*) junto com o código real do designer e painéis do designer.

**Isolamento de superfície** é usado pelo designer de UWP. Ele também é usado pelo designer do WPF para projetos destinados ao .NET Core. Superfície isoladamente, as bibliotecas de código e o controle de usuário somente são carregadas em um processo separado, enquanto o designer e seus painéis são carregados no processo do Visual Studio (*DevEnv.exe*). O tempo de execução usado para a execução de bibliotecas de código e o controle de usuário é diferente daquele usado pelo .NET Framework para o designer real e o código de extensibilidade de terceiros.

![arquitetura de migração de extensibilidade](media/xaml-designer-extensibility-migration-architecture.png)

Devido a essa transição de arquitetura, extensões de terceiros não são carregadas no mesmo processo que as bibliotecas de controle de terceiros. As extensões não podem ter dependências diretas em bibliotecas de controle ou acessar diretamente os objetos de tempo de execução. Extensões que foram previamente gravadas para a arquitetura de designer isolamento usando o *Microsoft.Windows.Extensibility.dll* API deve ser migrada para uma nova abordagem para trabalhar com a arquitetura de isolamento de superfície. Na prática, uma extensão existente precisará ser compilado em relação a novos assemblies de API de extensibilidade. Tipos de acesso para controle de tempo de execução por meio [typeof](/dotnet/csharp/language-reference/keywords/typeof) ou instâncias de tempo de execução devem ser substituídas ou removidas porque as bibliotecas de controle agora são carregadas em um processo diferente.

## <a name="new-extensibility-api-assemblies"></a>Novos assemblies de API de extensibilidade

Os novos assemblies de API de extensibilidade são semelhantes para os assemblies de API de extensibilidade existentes, mas seguem um esquema de nomenclatura diferente para diferenciá-los. Da mesma forma, os nomes de namespace foram alterados para refletir os novos nomes de assembly.

| Isolamento de designer assembly da API            | Assembly de isolamento de superfície API                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Descoberta e a nova extensão de arquivo

Em vez de usar o *. dll* extensão, a nova superfície extensões serão descobertas por meio de arquivo a *. designtools.dll* extensão de arquivo. *. dll* e *. designtools.dll* extensões podem existir na mesma *Design* subpasta.

Embora as bibliotecas de controle de terceiros são compiladas para o tempo de execução real de destino (.NET Core ou UWP), o *. designtools.dll* extensão sempre deve ser compilada como um assembly do .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Desacoplar as tabelas de atributos de tipos de tempo de execução

Não permite que o modelo de extensibilidade do isolamento de superfície para que as extensões dependem de bibliotecas de controle real e, portanto, as extensões não podem referenciar tipos da biblioteca de controle. Por exemplo, *MyLibrary.designtools.dll* não deve ter uma dependência na *MyLibrary*.

Essas dependências eram mais comuns ao registrar os metadados para tipos por meio de tabelas de atributo. Tipos de código de extensão que faz referência a biblioteca de controle diretamente por meio [typeof](/dotnet/csharp/language-reference/keywords/typeof) ou [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) será substituído nas novas APIs por meio de nomes de tipo com base em cadeia de caracteres:

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

## <a name="feature-providers-and-model-api"></a>Provedores de recursos e a API de modelo

Provedores de recursos são implementados em assemblies de extensão e carregados no processo do Visual Studio. `FeatureAttribute` continuará a fazer referência a tipos de provedor de recurso diretamente, usando [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Atualmente, há suporte para os seguintes provedores de recurso:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`

Porque agora são carregados em um processo diferente de bibliotecas de código e controle o tempo de execução real de provedores de recursos, eles não são mais capazes de acessar objetos de tempo de execução diretamente. Em vez disso, todas essas interações devem ser convertidas para usar as APIs correspondentes com base no modelo. A API de modelo foi atualizado e o acesso ao <xref:System.Type> ou <xref:System.Object> é não está mais disponível ou foi substituído por `TypeIdentifier` e `TypeDefinition`.

`TypeIdentifier` representa uma cadeia de caracteres sem um nome de assembly identificando um tipo. Um `TypeIdenfifier` pode ser resolvido para um `TypeDefinition` para obter informações adicionais sobre o tipo de consulta. `TypeDefinition` instâncias não podem ser armazenados em cache no código de extensão.

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

APIs removidas do conjunto de API de extensibilidade de isolamento de superfície:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

As APIs que usam `TypeIdentifier` em vez de <xref:System.Type>:

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

As APIs que usam `TypeIdentifier` em vez de <xref:System.Type> e não há mais suporte a argumentos de construtor:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

As APIs que usam `TypeDefinition` em vez de <xref:System.Type>:

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

As APIs que usam `ModelItem` em vez de <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Conhecido como tipos primitivos `Int32`, `String`, ou `Thickness` pode ser passado para a API do modelo como instâncias do .NET Framework e será convertido para o objeto correspondente no processo de tempo de execução de destino. Por exemplo:

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

Mais exemplos de código estão disponíveis na [xaml-designer-exemplos de extensibilidade](https://github.com/microsoft/xaml-designer-extensibility-samples) repositório.

## <a name="limited-support-for-designdll-extensions"></a>Suporte limitado para. dll extensões

Se houver *. designtools.dll* extensão é descoberta para uma biblioteca de controle, ele é carregado primeiro e descoberta para *. dll* extensões é ignorada.

Se nenhum *. designtools.dll* extensões estiverem presentes, mas um *. dll* extensão for encontrada, o serviço de linguagem XAML tenta carregar esse assembly para extrair as informações da tabela para dar suporte ao atributo editor básico e cenários de Inspetor de propriedade. Esse mecanismo é limitado em escopo. Ele não permite o carregamento de extensões do designer de isolamento para executar os provedores de recursos, mas pode fornecer suporte básico para bibliotecas de controles WPF existentes.
