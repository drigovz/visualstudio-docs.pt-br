---
title: Como exibir uma lista de itens separada por vírgula | Microsoft Docs
description: Saiba como usar o MSBuild para exibir uma lista de itens separados por vírgulas ou especificar outras cadeias de caracteres separadoras para uma lista de itens.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ac0295b2d6f4300fa29c893d61616977ad44b87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914420"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Como exibir uma lista de itens separados por vírgulas

Quando você trabalha com listas de itens no Microsoft Build Engine (MSBuild), às vezes é útil exibir o conteúdo dessas listas de itens de forma que seja fácil de ler. Ou, você pode ter uma tarefa que utiliza uma lista de itens separados por uma cadeia de caracteres do separador especial. Em ambos os casos, você pode especificar uma cadeia de caracteres do separador para uma lista de itens.

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

Neste exemplo, a tarefa [Exec](../msbuild/exec-task.md) executa a ferramenta findstr para localizar as cadeias de caracteres de texto especificadas no arquivo *Phrases.txt*. No comando Findstr, as cadeias de caracteres de pesquisa literais são indicadas pela opção **-c:** , portanto, o separador de item `-c:` é inserido entre os itens na `@(Phrase)` lista de itens.

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
