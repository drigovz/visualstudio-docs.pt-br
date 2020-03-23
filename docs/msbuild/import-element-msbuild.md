---
title: Elemento Import (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d9e66934015c7c4a57c7d7c6911b9ebe02ac536
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094493"
---
# <a name="import-element-msbuild"></a>Elemento Import (MSBuild)

Importa o conteúdo de um arquivo de projeto para outro arquivo de projeto.

\<Project> \<Import>

## <a name="syntax"></a>Sintaxe

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Project`|Atributo obrigatório.<br /><br /> O caminho do arquivo de projeto para importar. O caminho pode incluir caracteres curinga. Os arquivos correspondentes são importados na ordem de classificação. Usando esse recurso, você pode adicionar o código a um projeto simplesmente adicionando o arquivo de código para um diretório.|
|`Condition`|Atributo opcional.<br /><br /> Uma condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|
|`Sdk`| Atributo opcional.<br /><br /> Faz referência a um projeto do SDK.|

### <a name="child-elements"></a>Elementos filho

 Nenhum

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto MSBuild. |
| [ImportGroup](../msbuild/importgroup-element.md) | Contém uma coleção de elementos `Import` agrupados em uma condição opcional. |

## <a name="remarks"></a>Comentários

 Ao usar o elemento `Import`, você pode reutilizar o código que é comum a vários arquivos de projeto. Isso facilita a manutenção do código porque as atualizações feitas no código compartilhado são propagadas a todos os projetos o importam.

 Por convenção, arquivos de projeto importados compartilhados são salvos como arquivos *.targets,* mas são arquivos de projeto MSBuild padrão. O MSBuild não impede que você importe um projeto que tenha uma extensão de nome de arquivo diferente, mas recomendamos que você use a extensão *.targets* para consistência.

 Caminhos relativos em projetos importados são interpretados em relação ao diretório do projeto de importação (com algumas exceções descritas posteriormente neste parágrafo). Portanto, se um arquivo de projeto for importado em vários arquivos de projeto em locais diferentes, os caminhos relativos no arquivo de projeto importado serão interpretados de maneira diferente para cada projeto importado. Há duas exceções. Uma exceção `Import` é que, em elementos, o caminho `Import` é sempre interpretado em relação ao projeto que contém o elemento. Outra exceção `UsingTask` é que o sempre `AssemblyFile` interpreta o caminho relativo `UsingTask` para o atributo em relação ao arquivo que contém o elemento.

 Todas as propriedades reservadas do MSBuild que `MSBuildProjectDirectory` `MSBuildProjectFile`se relacionam com o arquivo do projeto, por exemplo, e , que são referenciadas em um projeto importado são valores atribuídos com base no arquivo do projeto de importação.

 Se o projeto importado não tiver um atributo `DefaultTargets`, os projetos importados serão inspecionados na ordem em que forem importados e o valor do primeiro atributo `DefaultTargets` descoberto será usado. Por exemplo, se o ProjectA importa ProjectB e ProjectC (nessa ordem), e `DefaultTargets` o ProjectB importa ProjectD, o MSBuild primeiro procura especificado no ProjectA, depois ProjectB, depois ProjectD e, finalmente, ProjectC.

 O esquema de um projeto importado é idêntico ao de um projeto padrão. Embora o MSBuild possa ser capaz de construir um projeto importado, é improvável porque um projeto importado normalmente não contém informações sobre quais propriedades definir ou a ordem em que executar alvos. O projeto importado depende do projeto para o qual ele é importado para fornecer essas informações.

## <a name="wildcards"></a>Curingas

 No .NET Framework 4, o MSBuild permite caracteres curinga no atributo Projeto. Quando houver caracteres curinga, todas as correspondências encontradas são classificadas (para capacidade de reprodução) e, em seguida, elas são importadas na ordem como se a ordem tivesse sido definida explicitamente.

 Isso é útil se você quiser oferecer um ponto de extensibilidade para que outra pessoa possa importar um arquivo sem exigir que você adicione explicitamente o nome do arquivo ao arquivo de importação. Para essa finalidade, o *Microsoft.Common.Targets* contém a linha a seguir na parte superior do arquivo.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra um projeto que tem vários itens e propriedades e importa um arquivo de projeto geral.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Como usar o mesmo destino em vários arquivos de projeto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
