---
title: Aplicar edições no modo de interrupção com editar e continuar | Microsoft Docs
Description: Consulte como usar editar e continuar para editar seu código de Visual Basic quando estiver no modo de interrupção. Há várias maneiras de entrar no modo de interrupção.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b8e6ef8c41fbaf5aafa6b1fc9ef4216c773e75e
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398682"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Como aplicar edições no modo de interrupção com editar e continuar (Visual Basic)
Você pode usar Editar e Continuar para editar o código no modo de interrupção e, depois, continuar sem interromper e reiniciar a execução.

Para obter limitações sobre como usar editar e continuar durante a depuração, consulte [alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Para editar código no modo de interrupção

1. Entre no modo de interrupção executando um destes procedimentos:

    - Defina um ponto de interrupção no código e escolha **Iniciar Depuração** no menu **Depurar** e aguarde até que o aplicativo atinja o ponto de interrupção.

         -ou-

    - Inicie a depuração e, em seguida, selecione **Interromper Tudo** no menu **Depurar**.

         -ou-

    - Quando ocorrer uma exceção, escolha **Habilitar edição** no **Assistente de exceção**.

2. Faça as alterações de código desejadas e com suporte.

     Para obter mais informações, consulte [alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Se você tentar fazer uma alteração de código que não seja permitida por Editar e Continuar, sua edição será sublinhada por uma linha ondulada roxa e uma tarefa será exibida na Lista de Tarefas. Você não poderá continuar a execução do código a menos que desfaça a alteração de código ilegal.

3. No menu **Depurar**, clique em **Continuar** para retomar a execução.

     O código agora é executado com as edições aplicadas incorporadas ao projeto.

## <a name="see-also"></a>Consulte também
- [Alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Editar e Continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
