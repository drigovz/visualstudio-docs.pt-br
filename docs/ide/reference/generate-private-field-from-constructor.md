---
title: Gerar campo particular do construtor
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094020"
---
# <a name="generate-private-field-from-constructor"></a>Gerar campo particular do construtor

Esta refatoração aplica-se a: 

- C# 

- Visual Basic

**O que é isso?** Gerar um campo privado a partir de um construtor. 

**Quando:** Você deseja adicionar rapidamente um campo privado de um construtor.

**Por que:** Escrever campos privados pode ser demorado e repetitivo. O uso dessa refatoração é rápido e torna o programa mais robusto.

## <a name="how-to"></a>Como fazer 

1. Coloque o cursor no nome do parâmetro dentro do construtor.

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   
3. Selecione a opção **Para Criar e inicializar o campo**.

   ![Gerar campo particular do construtor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Confira também 

- [Refatoração](../refactoring-in-visual-studio.md)
