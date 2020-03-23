---
title: Condições do MSBuild | Microsoft Docs
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
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e69e5c8fc7404c0c313774271fd07b6315e5270
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633363"
---
# <a name="msbuild-conditions"></a>Condições do MSBuild

O MSBuild suporta um conjunto específico de condições `Condition` que podem ser aplicadas onde um atributo é permitido. A tabela a seguir explica essas condições.

|Condição|Descrição|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Avaliará como `true` se `stringA` for igual a `stringB`.<br /><br /> Por exemplo: <br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios.|
|'`stringA`' != '`stringB`'|Avaliará como `true` se `stringA` não for igual a `stringB`.<br /><br /> Por exemplo: <br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios.|
|\<, >, \<=, >=|Avalia os valores numéricos dos operandos. Retornará `true` se a avaliação relacional for true. Os operandos devem ser avaliados como um número decimal ou hexadecimal. Os números hexadecimais devem começar com "0x". **Observação:** no XML, os caracteres `<` e `>` devem ser escapados. O símbolo `<` é representado como `&lt;`. O símbolo `>` é representado como `&gt;`.|
|Exists('`stringA`')|Avaliará como `true` se existir um arquivo ou pasta com o nome `stringA`.<br /><br /> Por exemplo: <br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios.|
|HasTrailingSlash('`stringA`')|Avaliará como `true` se a cadeia de caracteres contiver um caractere de barra invertida (\\) ou de barra "/" à direita.<br /><br /> Por exemplo: <br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> As aspas simples não são necessárias para cadeias de caracteres alfanuméricas simples ou valores boolianos. No entanto, as aspas são necessárias para valores vazios.|
|!|Avaliará como `true` se o operando for avaliado como `false`.|
|And|Avaliará como `true` se ambos os operandos forem avaliados como `true`.|
|Ou|Avaliará como `true` se pelo menos um dos operandos for avaliado como `true`.|
|()|Mecanismo de agrupamento que será avaliado como `true` se as expressões contidas dentro forem avaliadas como `true`.|
|$if$ ( %expression% ), $else$, $endif$|Verifica se o `%expression%` especificado corresponde ao valor de cadeia de caracteres do parâmetro do modelo personalizado passado. Se a condição `$if$` for avaliada como `true`, suas declarações serão executadas, caso contrário, a condição `$else$` será verificada. Se a condição `$else$` for `true`, suas declarações serão executadas, caso contrário, a condição `$endif$` encerrará a avaliação da expressão.<br /><br /> Para exemplos de uso, consulte a lógica do parâmetro de modelo de [projeto/item do Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Confira também

- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Construções condicionais](../msbuild/msbuild-conditional-constructs.md)
- [Passo a passo: Criando um arquivo de projeto MSBuild do zero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
