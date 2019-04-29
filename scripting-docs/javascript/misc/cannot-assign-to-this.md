---
title: Não é possível atribuir a 'this' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a4ba5d852a7d131a88930dd66931c026074549b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946583"
---
# <a name="cannot-assign-to-this"></a>Não é possível designar a "isso"
Você tentou atribuir um valor para **isso**. **Isso** é um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palavra-chave que se refere a qualquer um:

- o objeto de um método em execução atualmente

- o objeto global, se não há nenhum método atual (ou o método não pertence a nenhum outro objeto).

Um método é um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] função que é invocada por meio de um objeto. Dentro de um método, o **isso** palavra-chave é uma referência ao objeto que o método foi invocado por meio (que é o objeto criado, invocando o construtor de classe com o **novos** operador).

Dentro de um método, você pode usar **isso** fazer referência ao objeto atual, mas não é possível atribuir um novo valor para **isso**.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Não tente atribuir a **isso**. Para acessar uma propriedade ou método de um objeto instanciado, use o operador ponto (por exemplo, **circle.radius**).

  > [!NOTE]
  > Você não pode nomear uma variável criada pelo usuário **isso**; ele é um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palavra reservada.

## <a name="see-also"></a>Consulte também

- [Instrução this](../../javascript/reference/this-statement-javascript.md)
- [Solucionar problemas com scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)