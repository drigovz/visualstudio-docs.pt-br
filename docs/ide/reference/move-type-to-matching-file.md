---
title: Mover um tipo para uma refatoração de arquivo correspondente
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 31e3b12f6a19ea64e43f7a5e00e3c795cc7358e0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55941030"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refatoração Mover um tipo para um arquivo correspondente

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** Permite mover o tipo selecionado para um arquivo separado com o mesmo nome.

**Quando:** Você tem várias classes, structs, interfaces, etc., no mesmo arquivo que deseja separar.

**Por que:** A colocação de vários tipos no mesmo arquivo pode dificultar a localização desses tipos. Ao mover os tipos de arquivos com o mesmo nome, o código torna-se mais legível e mais fácil de navegar.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor dentro do nome do tipo de onde ele está definido. Por exemplo:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Depois, siga um destes procedimentos:

   - Pressione **Ctrl**+**.**
   - Clique com o botão direito do mouse sobre o nome do tipo e selecione **Ação Rápidas e Refatorações**

1. Selecione **Mover tipo para *NomeDoTipo*.cs** no menu, em que *NomeDoTipo* é o nome do tipo selecionado.

   O tipo é movido para um novo arquivo no projeto que possui o mesmo nome do tipo.

   - C#:

      ![Resultado embutido – C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Resultado embutido – Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
