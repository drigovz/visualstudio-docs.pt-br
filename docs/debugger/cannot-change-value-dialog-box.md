---
title: Não é possível alterar a caixa de diálogo valor | Microsoft Docs
description: Examine a caixa de diálogo não é possível alterar o valor, que aparece no Visual Studio se você tentar alterar uma variável para um valor ilegal em uma janela do depurador ou QuickWatch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3dfedc12a1634e6f804c0cb3a9fceee9e9d43216
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857884"
---
# <a name="cannot-change-value-dialog-box"></a>Caixa de diálogo Não é Possível Alterar o Valor
## <a name="error"></a>Erro
 `The value of this variable cannot be changed` &#124; `The name` *nome* `does not exist in the current context` &#124; *várias outras mensagens*

 Essa caixa de mensagem aparece quando você tenta alterar o conteúdo de uma variável para um valor inválido em uma janela do depurador (janelas Autos, Inspeção ou Locais) ou na caixa de diálogo QuickWatch. Por exemplo, se você tentar definir o valor de uma variável de inteiro como uma cadeia de caracteres, essa caixa de mensagem é exibida.

## <a name="solution"></a>Solução
 Certifique-se que o valor inserido na janela do depurador ou na caixa de diálogo QuickWatch representa um valor válido para a variável que você está tentando definir.

## <a name="see-also"></a>Confira também

- [Expressões no depurador](../debugger/expressions-in-the-debugger.md)