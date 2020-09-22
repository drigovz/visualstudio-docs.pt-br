---
title: 'Como: aplicar edições no modo de interrupção com editar e continuar | Microsoft Docs'
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
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c04dc0ae6e5272d2544ad7436fa7ca516c9a022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838390"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Como aplicar edições no modo de interrupção com editar e continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar Editar e Continuar para editar o código no modo de interrupção e, depois, continuar sem interromper e reiniciar a execução.  
  
 Editar e Continuar não está disponível nos seguintes cenários de depuração:  
  
- Depuração de modo misto (nativo/gerenciado).  
  
- Depuração de SQL.  
  
- Depurando um despejo de Dr. Watson.  
  
- Editando o código após uma exceção sem tratamento quando a opção **Desenrolar a pilha de chamadas em exceções não tratadas** não está selecionada.  
  
- Depurando um aplicativo inserido de runtime.  
  
- Depuração de um aplicativo com **Attach to** em vez de executar o aplicativo com **Start** no menu **debug** .  
  
- Depurando código otimizado.  
  
- Depurando código gerenciado quando o destino é um aplicativo de 64 bits. Se você desejar usar Editar e Continuar, deve definir o destino como x86. (_Project_**Propriedades**do projeto, guia **Compilar** , configuração **avançada do compilador** .).  
  
- Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.  
  
### <a name="to-edit-code-in-break-mode"></a>Para editar código no modo de interrupção  
  
1. Entre no modo de interrupção executando um destes procedimentos:  
  
    - Defina um ponto de interrupção no código e escolha **Iniciar Depuração** no menu **Depurar** e aguarde até que o aplicativo atinja o ponto de interrupção.  
  
         –ou–  
  
    - Inicie a depuração e, em seguida, selecione **Interromper Tudo** no menu **Depurar**.  
  
         –ou–  
  
    - Quando ocorrer uma exceção, escolha **Habilitar edição** no**Assistente de exceção**.  
  
2. Faça as alterações de código desejadas e legais.  
  
     Para obter mais informações, consulte [edições sem suporte no Visual Basic editar e continuar](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    > Se você tentar fazer uma alteração de código que não seja permitida por Editar e Continuar, sua edição será sublinhada por uma linha ondulada roxa e uma tarefa será exibida na Lista de Tarefas. Você não poderá continuar a execução do código a menos que desfaça a alteração de código ilegal.  
  
3. No menu **Depurar**, clique em **Continuar** para retomar a execução.  
  
     O código agora é executado com as edições aplicadas incorporadas ao projeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Edições sem suporte no Visual Basic editar e continuar](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Editar e Continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
