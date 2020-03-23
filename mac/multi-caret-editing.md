---
title: Edição com vários cursores
description: Insira texto em vários locais ao editar código no Visual Studio for Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451443"
---
# <a name="multi-caret-editing"></a>Edição com vários cursores

A edição multi-caret permite adicionar _n_ número de pontos de inserção de uma só vez. Quando estiver no modo multicuidado, você pode adicionar carets adicionais ao documento, seja através de cliques no mouse ou através de comandos de teclado. O cuidador primário é denotado por um cursor vermelho, enquanto os cuidados secundários presentes em uma cor azul-claro. O modo de edição multicaret `ESC` pode ser desativado através da chave.

## <a name="enabling-multi-caret-editing"></a>Habilitando a edição multi-caret

### <a name="keyboard"></a>Teclado

Você é capaz de ativar o modo multi-caret através do teclado de várias maneiras. A tabela a seguir fornece os atalhos de teclado disponíveis para inserir modos específicos de edição multi-caret:

| Tecla de acesso  | Ação                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Insira o próximo caret correspondente    | 
|  ⌥⇧;   | Insira carets em todas as correspondências | 
|  ⌥⇧,   | Remova o último caret             | 
|  ⌥⇧/   | Mova-se último caret para baixo          | 

Cada um desses comportamentos está ancorado na posição atual do cuidador quando você invoca o comando. Por exemplo, se o cuidador estiver no início da palavra "nome" e você invocar "Inserir caretas em todos os matching" (;) cada instância da palavra "nome" no documento atual terá um caret inserido no início da palavra. Da mesma forma, se você invocar o comando "Inserir o próximo caret correspondente" (().)) então um caret será colocado na próxima instância da palavra "nome". Este comando pode ser invocado várias vezes.

![teclado multi-caret](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mouse/touchpad

Usando seu cursor, você é capaz de liberar pontos de inserção específicos para suas múltiplas caretas. Enquanto os atalhos do teclado estão vinculados a strings correspondentes, você pode inserir manualmente uma careta em qualquer lugar do documento com o cursor. Uma vez que os carets são definidos, cada um ecoará as entradas-chave que você digita no teclado.

Para usar o mouse para inserir vários caretas, você deve pressionar e segurar e clicar onde você gostaria que os carets fossem inseridos. Você estará no modo de inserção enquanto as teclas forem mantidas. Se você inserir um caret em um local incorreto, você pode remover o cuidado continuando a segurar e clicando na mesma área novamente. Uma vez que você tenha todos os caretas localizados onde você gostaria, pare de pressionar as teclas e comece a digitar. O GIF a seguir demonstra tanto a seleção de um conjunto de pontos de inserção quanto a remoção de pontos de set erroneamente.

![mouse multi-caret](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Confira também

- [Ações rápidas (Visual Studio no Windows)](/visualstudio/ide/quick-actions)
- [Refatorar o código (Visual Studio no Windows)](/visualstudio/ide/refactoring-in-visual-studio)
