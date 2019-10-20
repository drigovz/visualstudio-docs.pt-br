---
title: Mover um tipo para uma refatoração de arquivo correspondente
description: Mova o tipo para um arquivo separado com o mesmo nome. Clique com o botão direito do mouse no tipo, selecione Ações Rápidas e Refatorações e selecione Mover Tipo para <TypeName>.cs.
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ba822981ade5ebdc191732e0a32b02a9a4005fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666483"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refatoração Mover um tipo para um arquivo correspondente

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite mover o tipo selecionado para um arquivo separado com o mesmo nome.

**Quando:** você tem várias classes, structs, interfaces, etc. no mesmo arquivo que deseja separar.

**Por quê:** colocar vários tipos no mesmo arquivo pode dificultar a localização desses tipos. Ao mover os tipos de arquivos com o mesmo nome, o código torna-se mais legível e mais fácil de navegar.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor dentro do nome do tipo de onde ele está definido. Por exemplo:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Depois, siga um destes procedimentos:

   - Pressione **Ctrl**+ **.**
   - Clique com o botão direito do mouse sobre o nome do tipo e selecione **Ação Rápidas e Refatorações**

1. Selecione **Mover tipo para *NomeDoTipo*.cs** no menu, em que *NomeDoTipo* é o nome do tipo selecionado.

   O tipo é movido para um novo arquivo no projeto que possui o mesmo nome do tipo.

   - C#:

      ![Resultado embutido – C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Resultado embutido – Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
