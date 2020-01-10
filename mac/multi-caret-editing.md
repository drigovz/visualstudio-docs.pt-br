---
title: Edição com vários cursores
description: Inserir texto em vários locais ao editar código em Visual Studio para Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451443"
---
# <a name="multi-caret-editing"></a>Edição com vários cursores

A edição de vários argumentos permite adicionar _n_ número de pontos de inserção em uma única vez. Quando estiver no modo de cursor múltiplo, você poderá adicionar mais acentos ao documento por meio de cliques do mouse ou por meio de comandos de teclado. O cursor principal é indicado por um cursor vermelho, enquanto os sinais de interpolação secundários apresentam uma cor azul clara. O modo de edição de vários acentos pode ser desabilitado por meio da chave de `ESC`.

## <a name="enabling-multi-caret-editing"></a>Habilitando a edição de vários acento circunflexo

### <a name="keyboard"></a>Teclado

Você pode habilitar o modo de vários acentos por meio do teclado de várias maneiras. A tabela a seguir fornece os atalhos de teclado disponíveis para inserir modos específicos de edição com vários acentos:

| Tecla de acesso  | Action                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Inserir próximo cursor correspondente    | 
|  ⌥⇧;   | Inserir acento circunflexo em todas as correspondências | 
|  ⌥⇧,   | Remover último cursor             | 
|  ⌥⇧/   | Mover último cursor para baixo          | 

Cada um desses comportamentos é ancorado à posição atual do cursor quando você invoca o comando. Por exemplo, se o cursor estiver no início da palavra "nome" e você invocar "inserir Cursors em todas as correspondências" (⌥ ⇧;) cada instância da palavra "nome" no documento atual terá um cursor inserido no início da palavra. Da mesma forma, se você invocar o comando "inserir próximo cursor correspondente" (⌥ ⇧.), um cursor será colocado na próxima instância da palavra "Name". Esse comando pode ser invocado várias vezes.

![teclado de vários Cursors](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mouse/Touchpad

Usando o cursor, você pode liberar pontos de inserção específicos para seus vários acentos. Embora os atalhos de teclado estejam associados a cadeias de caracteres correspondentes, você pode inserir manualmente um cursor em qualquer lugar do documento com o cursor. Depois que os Cursors forem definidos, cada um irá ecoar as entradas de chave digitadas no teclado.

Para usar o mouse para inserir vários acentos, você deve pressionar e manter ⌘ ⌥ e clicar no local em que deseja que os acento circunflexo sejam inseridos. Você estará no modo de inserção, desde que as chaves ⌘ ⌥ sejam mantidas. Se você inserir um cursor em um local incorreto, poderá remover o cursor continuando a manter ⌘ ⌥ e clicando na mesma área novamente. Quando você tiver todos os acento circunflexo localizados onde desejar, pare de pressionar as chaves ⌘ ⌥ e comece a digitar. O GIF a seguir demonstra como selecionar um conjunto de pontos de inserção, bem como remover pontos definidos erroneamente.

![mouse com vários acentos](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Veja também

- [Ações rápidas (Visual Studio no Windows)](/visualstudio/ide/quick-actions)
- [Refatorar o código (Visual Studio no Windows)](/visualstudio/ide/refactoring-in-visual-studio)
