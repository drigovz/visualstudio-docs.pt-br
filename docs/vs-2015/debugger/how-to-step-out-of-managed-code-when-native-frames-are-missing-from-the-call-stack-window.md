---
title: 'Como: Sair do código gerenciado quando quadros nativos estiverem ausentes da janela pilha de chamadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1672ba8e6bcf66973a5cd32be3fb03821750e3f2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442744"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Como: Sair do código gerenciado quando quadros nativos estiverem ausentes na janela Pilha de Chamadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se seu código tiver quadros nativos invisíveis na janela **Pilha de Chamadas**, realizar a depuração circular do código gerenciado poderá produzir resultados inesperados. Como alternativa, você pode usar um ponto de interrupção em vez da **Depuração Circular**.  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Para depurar fora do código gerenciado quando os quadros nativos estiverem ausentes da exibição da pilha de chamadas  
  
1. No código nativo, defina um ponto de interrupção do local depois da chamada para o código gerenciado.  
  
2. No menu **Depurar**, escolha **Continuar**.  
  
     Quando a chamada gerenciada for concluída, a execução será interrompida no ponto de interrupção no código nativo.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Usar a janela de pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md)
