---
title: 'Como: Aplicar edições no modo de interrupção com editar e continuar | Microsoft Docs'
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
ms.openlocfilehash: e26b293a5ac7326ca8f82250ec3d0da9fe96371c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069920"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Como: Aplicar edições no modo de interrupção com editar e continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar Editar e Continuar para editar o código no modo de interrupção e, depois, continuar sem interromper e reiniciar a execução.  
  
 Editar e Continuar não está disponível nos seguintes cenários de depuração:  
  
- Depuração de modo misto (nativo/gerenciado).  
  
- Depuração de SQL.  
  
- Depurando um despejo do Dr. Watson.  
  
- Editando o código após uma exceção sem tratamento quando a opção **Desenrolar a pilha de chamadas em exceções não tratadas** não está selecionada.  
  
- Depurando um aplicativo inserido de tempo de execução.  
  
- Depurando um aplicativo com **anexar** em vez de executar o aplicativo com **iniciar** do **depurar** menu.  
  
- Depurando código otimizado.  
  
- Depurando código gerenciado quando o destino é um aplicativo de 64 bits. Se você desejar usar Editar e Continuar, deve definir o destino como x86. (_Projeto_**Properties**, **compilar** guia **avançado compilador** configuração.).  
  
- Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.  
  
### <a name="to-edit-code-in-break-mode"></a>Para editar código no modo de interrupção  
  
1. Entre no modo de interrupção executando um destes procedimentos:  
  
    - Defina um ponto de interrupção no código e escolha **Iniciar Depuração** no menu **Depurar** e aguarde até que o aplicativo atinja o ponto de interrupção.  
  
         – ou –  
  
    - Inicie a depuração e, em seguida, selecione **Interromper Tudo** no menu **Depurar**.  
  
         – ou –  
  
    - Quando ocorre uma exceção, escolha **habilitar edição** sobre o**Assistente de exceção**.  
  
2. Faça as alterações de código desejadas e legais.  
  
     Para obter mais informações, consulte [edições sem suporte no Visual Basic Edit and Continue](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Se você tentar fazer uma alteração de código que não seja permitida por Editar e Continuar, sua edição será sublinhada por uma linha ondulada roxa e uma tarefa será exibida na Lista de Tarefas. Você não poderá continuar a execução do código a menos que desfaça a alteração de código ilegal.  
  
3. No menu **Depurar**, clique em **Continuar** para retomar a execução.  
  
     O código agora é executado com as edições aplicadas incorporadas ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Edições sem suporte no Visual Basic, editar e continuar](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Editar e Continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
