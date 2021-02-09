---
title: Condições do MSBuild | Microsoft Docs
description: Saiba como o MSBuild dá suporte a um conjunto específico de condições que podem ser aplicadas sempre que um atributo de condição for permitido.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a480c539fc178e5ae672427fe32e9fd34728dc79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919158"
---
# <a name="msbuild-conditions"></a>Condições do MSBuild

O MSBuild dá suporte a um conjunto específico de condições que podem ser aplicadas sempre que um `Condition` atributo é permitido. A tabela a seguir explica essas condições.

|Condição|Descrição|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Avaliará como `true` se `stringA` for igual a `stringB`.<br /><br /> Por exemplo:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios. Essa verificação não diferencia maiúsculas de minúsculas.|
|'`stringA`' != '`stringB`'|Avaliará como `true` se `stringA` não for igual a `stringB`.<br /><br /> Por exemplo:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios. Essa verificação não diferencia maiúsculas de minúsculas.|
|\<, >, \<=, >=|Avalia os valores numéricos dos operandos. Retornará `true` se a avaliação relacional for true. Os operandos devem ser avaliados como um número decimal ou hexadecimal. Os números hexadecimais devem começar com "0x". **Observação:** no XML, os caracteres `<` e `>` devem ser escapados. O símbolo `<` é representado como `&lt;`. O símbolo `>` é representado como `&gt;`.|
|Exists('`stringA`')|Avaliará como `true` se existir um arquivo ou pasta com o nome `stringA`.<br /><br /> Por exemplo:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios.|
|HasTrailingSlash('`stringA`')|Avaliará como `true` se a cadeia de caracteres contiver um caractere de barra invertida (\\) ou de barra "/" à direita.<br /><br /> Por exemplo:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios.|
|!|Avaliará como `true` se o operando for avaliado como `false`.|
|`And`|Avaliará como `true` se ambos os operandos forem avaliados como `true`.|
|`Or`|Avaliará como `true` se pelo menos um dos operandos for avaliado como `true`.|
|()|Mecanismo de agrupamento que será avaliado como `true` se as expressões contidas dentro forem avaliadas como `true`.|
|$if$ ( %expression% ), $else$, $endif$|Verifica se o `%expression%` especificado corresponde ao valor de cadeia de caracteres do parâmetro do modelo personalizado passado. Se a condição `$if$` for avaliada como `true`, suas declarações serão executadas, caso contrário, a condição `$else$` será verificada. Se a condição `$else$` for `true`, suas declarações serão executadas, caso contrário, a condição `$endif$` encerrará a avaliação da expressão.<br /><br /> Para obter exemplos de uso, consulte [lógica de parâmetro de modelo de projeto/item do Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Você pode usar métodos de cadeia de caracteres em condições, conforme mostrado no exemplo a seguir, no qual a função [TrimEnd ()](/dotnet/api/system.string.trimend) é usada para comparar apenas a parte relevante da cadeia de caracteres, para diferenciar entre .NET Framework e estruturas de destino do .NET Core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

Em arquivos de projeto do MSBuild, não há nenhum tipo booliano verdadeiro. Os dados boolianos são representados nas propriedades que podem estar vazias ou definidas para qualquer valor. Portanto, `'$(Prop)' == 'true'` significa "If prop is `true` ", mas `'$(Prop)' != 'false'` significa "If prop is `true` or undefineble or Set to outra coisa".

A lógica booliana é avaliada apenas no contexto de condições, de modo que as configurações de propriedade, como `<Prop2>'$(Prop1)' == 'true'</Prop>` são representadas como uma cadeia de caracteres (após a expansão da variável), não avaliadas como valores Boolianos.  

O MSBuild implementa algumas regras de processamento especiais para facilitar o trabalho com propriedades de cadeia de caracteres que são usadas como valores Boolianos. Os literais boolianos são aceitos, portanto, `Condition="true"` e `Condition="false"` funcionam conforme o esperado. O MSBuild também inclui regras especiais para dar suporte ao operador de negação booliana. Portanto, se `$(Prop)` for ' true ', `!$(Prop)` expandirá para `!true` e isso será comparado igual a `false` , como você esperaria.

## <a name="see-also"></a>Confira também

- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Construções condicionais](../msbuild/msbuild-conditional-constructs.md)
- [Passo a passo: Criar um arquivo de projeto do MSBuild do zero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
