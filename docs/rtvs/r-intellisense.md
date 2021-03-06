---
title: IntelliSense para código em R
description: O Visual Studio IntelliSense exibe informações sobre funções, membros do objeto, snippets de código e conclusões conforme você digita o código R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: de6a8ffbaa0fb10929d013a351ebffa8e3f4b529
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939429"
---
# <a name="intellisense"></a>IntelliSense

O Visual Studio IntelliSense exibe informações sobre funções que você pode chamar, membros dos objetos, argumentos de função e [snippets de código](code-snippets-for-r.md) diretamente em sua exibição ao escrever código. Ele também exibe as conclusões possíveis à medida que você digita e é concluído quando você pressiona a **tecla Tab** ou **digita** as teclas (consulte [as opções do editor](editing-r-code-in-visual-studio.md#editor-options) para a guia **avançado** ). O IntelliSense está disponível no editor e na [janela interativa](interactive-repl-for-r-in-visual-studio.md).

![IntelliSense mostrando uma assinatura de função](media/intellisense-function-signature.png)

Ao digitar uma função ou outra instrução, o IntelliSense fornece um menu de preenchimento automático filtrado (diferenciando maiúsculas de minúsculas ), de acordo com o que você já inseriu:

![Menu de preenchimento automático do IntelliSense](media/intellisense-auto-complete-menu.png)

Pressionar **Tab** (ou **Enter** ou **Space**, dependendo de como as opções são definidas), insere o item selecionado na lista suspensa. Você pode alterar a seleção com as teclas de direção.

O IntelliSense também oferece sugestões para membros dos objetos R:

![Sugestões do IntelliSense para membros do objeto](media/intellisense-auto-complete-r-objects.png)

Pressionar **ESC** ignora o menu completamente. Você pode trazê-lo de volta com o + **espaço** Ctrl.

Digitar o `(` de abertura para uma chamada de função insere o `)` de fechamento e abre a Ajuda de assinatura conforme mostrado anteriormente:

![Ajuda de assinatura do IntelliSense para uma função](media/intellisense-function-signature.png)

Novamente, **ESC** ignora o Popup; para assinaturas de função, você pode trazê-la novamente com **Ctrl** + **Shift** + **Space**.

> [!Tip]
> Se o parâmetro ajudar a obscurecer o texto abaixo dele, pressione e mantenha pressionada a tecla **Ctrl** para tornar o texto de ajuda do parâmetro translúcida.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense para funções e variáveis definidas pelo usuário

O IntelliSense aplica-se a funções definidas pelo usuário no mesmo arquivo, incluindo o preenchimento de parâmetro de nome:

![IntelliSense para funções definidas pelo usuário](media/intellisense-same-file-functions.png)

![Preenchimento de parâmetro do IntelliSense para funções definidas pelo usuário](media/intellisense-parameter-completion.png)

O IntelliSense também se aplica a variáveis no mesmo arquivo e na sessão atual:

![Preenchimento de variável do IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> Na janela interativa, o IntelliSense considera apenas nomes na sessão do R atual e ignora os arquivos em seu projeto.

## <a name="code-suggestions"></a>Sugestões de código

Quando uma lâmpada (chamada de smart tag) aparece na margem, o Visual Studio está sugerindo que um atalho está disponível para uma ação bastante usada. Por exemplo, passe o mouse sobre uma linha que contém uma instrução `library` no editor para ver uma lâmpada. Selecionar a lâmpada exibe as opções disponíveis:

![Smart tags para R no editor](media/intellisense-smart-tags.png)
