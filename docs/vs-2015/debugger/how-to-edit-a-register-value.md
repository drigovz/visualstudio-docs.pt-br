---
title: 'Como: editar um valor de registro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f0cd04b054d51119f6f6c1b0275c4f781656bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838535"
---
# <a name="how-to-edit-a-register-value"></a>Como editar um valor de registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela Registros só ficará disponível se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**.  
  
### <a name="to-change-the-value-of-a-register"></a>Para alterar o valor de um registro  
  
1. Na janela **Registros**, use a tecla TAB ou o mouse para mover o ponto de inserção para o valor que você deseja alterar. Quando você começa a digitar, o cursor deve estar localizado na frente do valor que você deseja substituir.  
  
2. Digite o novo valor.  
  
    > [!CAUTION]
    > Alterar valores do registro (principalmente nos registros de EIP e EBP) pode afetar a execução do programa.  
  
    > [!CAUTION]
    > Editar valores de ponto flutuante pode resultar em imprecisões secundárias devido à conversão decimal-binária de componentes fracionários. Mesmo uma edição aparentemente inócua pode resultar em alterações em alguns bits menos significativos no registro de um ponto flutuante.  
  
## <a name="see-also"></a>Consulte Também  
 [Como usar a janela Registros](../debugger/how-to-use-the-registers-window.md)
