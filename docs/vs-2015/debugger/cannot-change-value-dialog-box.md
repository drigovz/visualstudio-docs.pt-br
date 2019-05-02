---
title: Não é possível alterar a caixa de diálogo valor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfe275411346e499312ba51c50a3a2ac3f4ed7d5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925714"
---
# <a name="cannot-change-value-dialog-box"></a>Caixa de diálogo Não é Possível Alterar o Valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erro  
 `The value of this variable cannot be changed` &#124;`The name` *nome* `does not exist in the current context` &#124; *várias outras mensagens*  
  
 Essa caixa de mensagem aparece quando você tenta alterar o conteúdo de uma variável para um valor inválido em uma janela do depurador (janelas Autos, Inspeção ou Locais) ou na caixa de diálogo QuickWatch. Por exemplo, se você tentar definir o valor de uma variável de inteiro como uma cadeia de caracteres, essa caixa de mensagem é exibida.  
  
## <a name="solution"></a>Solução  
 Certifique-se que o valor inserido na janela do depurador ou na caixa de diálogo QuickWatch representa um valor válido para a variável que você está tentando definir.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões no depurador](../debugger/expressions-in-the-debugger.md)
