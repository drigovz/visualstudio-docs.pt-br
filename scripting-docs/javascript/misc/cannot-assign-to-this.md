---
title: Não é possível atribuir a 'this' | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f47778075b0395e4f0791d8f485188d40fab87a4
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802586"
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