---
title: Gerar campo particular do Construtor
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527657"
---
# <a name="generate-private-field-from-constructor"></a>Gerar campo particular do Construtor

Esta refatoração aplica-se a: 

- C# 

**O que:** Gerar um campo particular de um construtor. 

**Quando:** Você deseja adicionar rapidamente um campo particular de um construtor.

**Por que:** Escrever campos privados pode ser demorado e repetitivo. O uso dessa refatoração é rápido e torna o programa mais robusto.

## <a name="how-to"></a>Como fazer 

1. Coloque o cursor no nome do parâmetro dentro do construtor.

2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
   
3. Selecione a opção para **criar e inicializar o campo**.

   ![Gerar campo particular do Construtor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Confira também 

- [Refatoração](../refactoring-in-visual-studio.md)
