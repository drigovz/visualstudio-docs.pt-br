---
title: 'Como: Voltar para a função que chamou MFC em caso de interrupção | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 883fc1e4bd106ad067e3a9e412268860ed889e5c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438240"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Como: Retornar à função que chamou o MFC em caso de interrupção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se você usou o comando **Interromper** no menu **Depurar** para interromper o programa e terminou no MFC e se você tiver certeza de que o problema está no código, use a janela Pilha de Chamadas para retornar à função. Para obter mais informações, confira [Como: Usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 Às vezes seu código pode ser interrompido na bomba da mensagem. Nesse caso, não há nenhum código de usuário na pilha de chamadas. Para evitar esse problema, use pontos de interrupção (possivelmente com condições e contagens de ocorrências) em vez do comando **Interromper**. Para obter mais informações, consulte [pontos de interrupção e Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Para navegar até a função da qual o MFC foi chamado  
  
- Use a janela **Pilha de Chamadas**.  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)
