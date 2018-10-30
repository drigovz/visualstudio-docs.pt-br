---
title: 'Como: aplicar edições no modo de interrupção com editar e continuar | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 263e4bf4505995a4c8eccbe7c33f59115412dda5
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219504"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Como aplicar edições no modo de interrupção com editar e continuar
Você pode usar Editar e Continuar para editar o código no modo de interrupção e, depois, continuar sem interromper e reiniciar a execução.  
  
Para limitações sobre como usar Editar e continuar durante a depuração, consulte [Supported Code Changes (C# e Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>Para editar código no modo de interrupção  
  
1.  Entre no modo de interrupção executando um destes procedimentos:  
  
    -   Defina um ponto de interrupção em seu código, em seguida, escolha **iniciar depuração** da **depurar** menu e aguarde até que o aplicativo para o ponto de interrupção.  
  
         -ou-  
  
    -   Iniciar a depuração e, em seguida, selecione **interromper tudo** da **depurar** menu.  
  
         -ou-  
  
    -   Quando ocorre uma exceção, escolha **habilitar edição** sobre o **Assistente de exceção**.  
  
2.  Faça as alterações de código desejadas e com suporte.  
  
     Para obter mais informações, consulte [Supported Code Changes (c# e Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  Se você tentar fazer uma alteração de código que não seja permitida por Editar e Continuar, sua edição será sublinhada por uma linha ondulada roxa e uma tarefa será exibida na Lista de Tarefas. Você não poderá continuar a execução do código a menos que desfaça a alteração de código ilegal.  
  
3.  Sobre o **Debug** menu, clique em **continuar** para retomar a execução.  
  
     O código agora é executado com as edições aplicadas incorporadas ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de código suportadas (c# e Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Editar e Continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)