---
title: Como exibir uma lista de itens separada por vírgula | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5493d3b95f7e9c0aa08ed3b06a99108e15697349
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633896"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Como exibir uma lista de itens separados por vírgulas

Quando você trabalha com listas de itens no Microsoft Build Engine (MSBuild), às vezes é útil exibir o conteúdo dessas listas de itens de uma maneira fácil de ler. Ou, você pode ter uma tarefa que utiliza uma lista de itens separados por uma cadeia de caracteres do separador especial. Em ambos os casos, você pode especificar uma cadeia de caracteres do separador para uma lista de itens.

## <a name="separate-items-in-a-list-with-commas"></a>Separar itens em uma lista com vírgulas

Por padrão, o MSBuild usa ponto e vírgula para separar itens em uma lista. Por exemplo, considere um elemento `Message` com o seguinte valor:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Quando a lista de itens `@(TXTFile)` contém os itens *App1.txt*, *App2.txt* e *App3.txt*, a mensagem é:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Se você quiser alterar o comportamento padrão, especifique seu próprio separador. A sintaxe para especificar um separador de lista de itens é:

`@(ItemListName, '<separator>')`

O separador pode ser um único caractere ou uma cadeia de caracteres e deve ser colocado entre aspas.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Para inserir uma vírgula e um espaço entre itens

- Use a notação de item semelhante ao seguinte:

    `@(TXTFile, ', ')`

## <a name="example"></a>Exemplo

Neste exemplo, a tarefa [Exec](../msbuild/exec-task.md) executa a ferramenta findstr para localizar as cadeias de caracteres de texto especificadas no arquivo *Phrases.txt*. No comando findstr, as strings de pesquisa literal são indicadas pelo **-c:** switch, de modo que o separador do item, `-c:` seja inserido entre itens da `@(Phrase)` lista de itens.

Neste exemplo, a linha de comando equivalente é:

`findstr /i /c:hello /c:world /c:msbuild phrases.txt`

```xml
<Project DefaultTargets = "Find"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <Phrase Include="hello"/>
        <Phrase Include="world"/>
        <Phrase Include="msbuild"/>
    </ItemGroup>

    <Target Name = "Find">
        <!-- Find some strings in a file -->
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Itens](../msbuild/msbuild-items.md)
