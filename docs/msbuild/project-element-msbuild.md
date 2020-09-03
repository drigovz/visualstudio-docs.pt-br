---
title: Elemento Project (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632973"
---
# <a name="project-element-msbuild"></a>Elemento Project (MSBuild)

Elemento raiz necessário de um arquivo de projeto do MSBuild.

## <a name="syntax"></a>Sintaxe

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

| Atributo | Descrição |
|------------------------| - |
| `DefaultTargets` | Atributo opcional.<br /><br /> Os destinos padrão serão o ponto de entrada do build se nenhum destino for especificado. Vários destinos são separados por ponto e vírgula (;).<br /><br /> Se nenhum destino padrão for especificado no `DefaultTargets` atributo ou na linha de comando do MSBuild, o mecanismo executará o primeiro destino no arquivo de projeto depois que os elementos de [importação](../msbuild/import-element-msbuild.md) tiverem sido avaliados. |
| `InitialTargets` | Atributo opcional.<br /><br /> Os destinos iniciais serão executados antes dos destinos especificados no atributo `DefaultTargets` ou na linha de comando. Vários destinos são separados por ponto e vírgula (`;`). Se vários arquivos importados definirem `InitialTargets`, todos os destinos mencionados serão executados, na ordem em que as importações forem encontradas. |
| `Sdk` | Atributo opcional. <br /><br /> O nome e a versão opcional do SDK a ser usado para criar instruções Import implícitas adicionadas ao arquivo .proj. Se nenhuma versão for especificada, o MSBuild tentará resolver uma versão padrão.  Por exemplo, `<Project Sdk="Microsoft.NET.Sdk" />` ou `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Atributo opcional.<br /><br /> A versão do Conjunto de Ferramentas MSBuild usada para determinar os valores para $(MSBuildBinPath) e $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Atributo opcional.<br /><br /> Nomes de propriedade não serão considerados globais. Esse atributo impede que as propriedades específicas de linha de comando substituam valores de propriedade definidos em um arquivo de projeto ou destinos e todas as importações subsequentes. Várias propriedades são separadas por ponto e vírgula (;).<br /><br /> Normalmente, propriedades globais substituem os valores de propriedade que são definidos no arquivo de projeto ou destinos. Se a propriedade está listada no valor `TreatAsLocalProperty`, o valor da propriedade global não substitui os valores de propriedade definidos no arquivo e as importações subsequentes. Para obter mais informações, consulte [como: compilar os mesmos arquivos de origem com opções diferentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Observação:**  Defina as propriedades globais em um prompt de comando usando a opção **-Property** (ou **-p**). Você também pode definir ou modificar as propriedades globais para projetos filho em um build de vários projetos usando o atributo `Properties` da tarefa MSBuild. Para obter mais informações, consulte [MSBuild Task](../msbuild/msbuild-task.md). |
| `xmlns` | Atributo opcional.<br /><br /> Quando especificado, o atributo `xmlns` deve ter o valor `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Elementos filho

| Elemento | Descrição |
| - | - |
| [Escolha](../msbuild/choose-element-msbuild.md) | Elemento opcional.<br /><br /> Avalia a elementos filho para selecionar um conjunto de elementos `ItemGroup` e/ou `PropertyGroup` a ser avaliado. |
| [Importaçãoação](../msbuild/import-element-msbuild.md) | Elemento opcional.<br /><br /> Permite que um arquivo de projeto importe outro arquivo de projeto. Pode ser que não haja nenhum ou mais de um elemento `Import` em um projeto. |
| [ImportGroup](../msbuild/importgroup-element.md) | Elemento opcional.<br /><br /> Contém uma coleção de elementos `Import` que são agrupados em uma condição opcional. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Elemento opcional.<br /><br /> Um elemento de agrupamento para itens individuais. Itens são especificados usando o elemento [Item](../msbuild/item-element-msbuild.md). Pode ser que não haja nenhum ou mais de um elemento `ItemGroup` em um projeto. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Elemento opcional.<br /><br /> Permite definir um conjunto de Definições de Item, que são valores de metadados aplicados por padrão a todos os itens do projeto. ItemDefinitionGroup substitui a necessidade de usar as tarefas `CreateItem` e `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Elemento opcional.<br /><br /> Fornece uma maneira de persistir informações não MSBuild em um arquivo de projeto do MSBuild. Pode ser que não haja nenhum ou um elemento `ProjectExtensions` em um projeto. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Elemento opcional.<br /><br /> Um elemento de agrupamento para propriedades individuais. Propriedades são especificadas usando o elemento [Property](../msbuild/property-element-msbuild.md). Pode ser que não haja nenhum ou mais de um elemento `PropertyGroup` em um projeto. |
| [SDK](../msbuild/sdk-element-msbuild.md) | Elemento opcional.<br /><br /> Faz referência a um SDK de projeto do MSBuild.  Esse elemento pode ser usado como uma alternativa para o atributo Sdk. |
| [Target (destino)](../msbuild/target-element-msbuild.md) | Elemento opcional.<br /><br /> Contém um conjunto de tarefas para o MSBuild ser executado em sequência. Tarefas são especificadas usando o elemento [Task](../msbuild/task-element-msbuild.md). Pode ser que não haja nenhum ou mais de um elemento `Target` em um projeto. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Elemento opcional.<br /><br /> Fornece uma maneira de registrar tarefas no MSBuild. Pode ser que não haja nenhum ou mais de um elemento `UsingTask` em um projeto. |

### <a name="parent-elements"></a>Elementos pai

 Nenhum.

## <a name="see-also"></a>Confira também

- [Como especificar qual destino deve ser compilado primeiro](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
