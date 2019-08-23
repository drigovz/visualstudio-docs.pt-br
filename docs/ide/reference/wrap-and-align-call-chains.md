---
title: Encapsular e alinhar cadeias de chamadas
description: Saiba como encapsular e alinhar cadeias de chamadas de métodos.
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620008"
---
# <a name="wrap-and-align-call-chains"></a>Encapsular e alinhar cadeias de chamadas

Esta refatoração aplica-se a:

- C#

**O quê:** Saiba como encapsular e alinhar cadeias de chamadas de métodos.

**Quando:** Você tem uma cadeia longa que consiste em várias chamadas a método em uma única instrução.

**Por que:** Ler uma longa lista fica mais fácil quando os itens são encapsulados ou recuados de acordo com as preferências do usuário.

## <a name="how-to"></a>Como fazer

1. Posicione o cursor em qualquer uma das cadeias de chamadas.
2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Encapsular cadeia de chamadas** ou **Encapsular e alinhar cadeia de chamadas** para aceitar a refatoração.

   ![Encapsular e alinhar cadeias de chamadas](media/wrap-call-chain.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
