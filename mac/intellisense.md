---
title: IntelliSense
description: Informações sobre como usar o IntelliSense no Visual Studio para Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 3e99c31b1ab4d12532d701e4626ac9c1aae7df56
ms.sourcegitcommit: 0bd63f3bc429ae059b9df6e45c6b8dcae6152940
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026565"
---
# <a name="intellisense"></a>IntelliSense

O IntelliSense fornece vários recursos para ajudar a aprimorar a experiência de escrever e editar o código. Por exemplo, além do preenchimento de código, o mecanismo IntelliSense também fornece listas de membros, informações de parâmetros e informações rápidas.

No Visual Studio para Mac, o IntelliSense é fornecido pelo serviço de editor principal e é compatível com várias linguagens, como C#, XAML, F#, JavaScript, entre outros. O Visual Studio para Mac também apresenta recursos avançados do IntelliSense, como a capacidade de mostrar os preenchimentos de bibliotecas que ainda não foram importadas para o projeto.

## <a name="code-completion"></a>Preenchimento de código

Ao digitar em um arquivo compatível, como um arquivo de código C#, os preenchimentos válidos para a cadeia de caracteres que você está digitando no momento serão exibidos em uma lista de conclusão e atualizados conforme você digitar. Além disso, se você excluir o texto, a lista será atualizada automaticamente para incluir o intervalo mais amplo de possibilidades para o preenchimento da cadeia de caracteres especificada. 

A janela de conclusão também oferece suporte para filtrar os preenchimentos incluídos por tipo. Por exemplo, é possível limitar os membros da lista para representar apenas tipos como classes ou representantes. Esse processo de filtragem pode ser habilitado por meio de um clique em um ícone específico que representa o tipo que será filtrado ou por meio de atalhos de teclado correspondentes a determinado tipo. Os ícones, que estão localizados na parte inferior da janela de conclusão, são os seguintes:

| Ícone                         | Nome          | Palavra-chave    | Tecla de acesso |
| -----------------------------|---------------| -----------|--------|
| ![Ícone de classes](media/classes-icon.png)  | classe         | `class`    |  ⌥C
| ![Ícone constante](media/constant-icon.png) | constante      | `const`    |  ⌥O
| ![Ícone de representante](media/delegate-icon.png) | delegado      | `delegate` |  ⌥D
| ![Ícone de enumeração](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![Ícone de evento](media/event-icon.png)    | evento         |            |  ⌥V
| ![Ícone de campo](media/fields-icon.png)   | campo         |            |  ⌥F
| ![Ícone de interface](media/interface-icon.png)| interface     | `interface`|  ⌥I
| ![Ícone de palavra-chave](media/keyword-icon.png)  | keyword       |            |  ⌥K
| ![Ícone de método](media/method-icon.png)   | method        |            |  ⌥M
| ![Ícone de namespace](media/namespace-icon.png)| namespace     | `namespace`|  ⌥N
| ![Ícone de propriedades](media/props-icon.png)    | propriedade      |            |  ⌥P
| ![Ícone de snippet](media/snippet-icon.png)  | snippet       | `class`    |  ⌥S
| ![Ícone de struct](media/struct-icon.png)   | Estrutura     | `struct`   |  ⌥S

Ao clicar em um dos ícones ou ao pressionar as teclas de acesso correspondentes, a lista de conclusão será limitada somente aos tipos definidos pelo conjunto de filtros.  

![Filtragem de tipo do IntelliSense](media/intellisense-typefiltering.gif)

## <a name="show-import-items"></a>Mostrar itens de importação

Por padrão, o preenchimento do IntelliSense exibirá apenas os preenchimentos de bibliotecas que foram importados para o projeto. Por exemplo, se você não tiver `System.Collections.Generic` importado por meio de `using`, não terá um preenchimento para `List<>`. Para exibir os preenchimentos de bibliotecas que não foram importados, é necessário habilitar **Mostrar Itens de Importação** nas Preferências do Visual Studio para Mac. Essa configuração pode ser encontrada em **Preferências > Editor de Texto > IntelliSense**:

![Mostrar Itens de Importação do IntelliSense](media/intellisense-showimport.png)

Depois que a opção **Mostrar Itens de Importação** for habilitada, a lista de conclusão incluirá os preenchimentos que ainda não foram importados. Ao selecionar um item que corresponde a uma biblioteca não declarada, a instrução `using` para essa biblioteca será automaticamente adicionada ao cabeçalho do arquivo de código. O nome da biblioteca à qual pertence o preenchimento também é listado junto com o próprio preenchimento.

![Mostrar Lista de Itens de Importação](media/intellisense-importaction.png)

## <a name="parameter-window"></a>Janela de Parâmetros

Outro recurso do IntelliSense é a capacidade de fornecer uma lista de parâmetros, quando apropriado. A lista de parâmetros fornece detalhes das assinaturas de método para o código que está sendo chamado. Ao clicar nas setas para cima/para baixo na assinatura, você pode percorrer cada uma das assinaturas de parâmetro disponíveis para determinar as mais adequadas às suas necessidades. Além dos detalhes dos tipos de dados permitidos, também pode haver uma descrição, conforme definido no método de destino por meio de comentários XML.

![Lista de parâmetros](media/intellisense-parameter.png)

Conforme você preenche os parâmetros, o parâmetro que você está editando no momento ficará em negrito, enquanto os parâmetros inativos terão o peso padrão. 


## <a name="triggering-completion-window-and-parameter-window"></a>Como disparar a Janela de Conclusão e a Janela de Parâmetros

A janela de conclusão é disparada automaticamente conforme você digita no arquivo de origem. No entanto, você também pode disparar a janela de conclusão usando o atalho `control-space`. Essa combinação de teclas fará com que a lista de conclusão apareça na posição atual do cursor. 

Dispare também manualmente a aparência da janela de parâmetros digitando `control-shift-space`. Quando o cursor estiver na posição que é válida para uma lista de parâmetros, a lista de parâmetros será exibida próximo à posição do cursor.

## <a name="see-also"></a>Consulte também

- [Ações rápidas (Visual Studio no Windows)](/visualstudio/ide/quick-actions)
- [Refatorar o código (Visual Studio no Windows)](/visualstudio/ide/refactoring-in-visual-studio)