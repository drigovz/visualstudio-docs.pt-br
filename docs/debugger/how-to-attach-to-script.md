---
title: 'Como: anexar ao Script | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05d2a2cbd3cfe59b1d110fdd8b0b7c5fd042d25c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937321"
---
# <a name="how-to-attach-to-script"></a>Como anexar ao script
Este tópico explica como anexar manualmente o depurador do Visual Studio para um arquivo de script para depuração.  
  
### <a name="to-attach-to-a-running-process"></a>Para anexar a um processo em execução  
  
1. No menu **Depurar**, escolha **Anexar ao Processo**. (Se nenhum projeto estiver aberto, escolha **Anexar ao Processo** no menu **Ferramentas**.)  
  
2. Na caixa de diálogo **Anexar ao Processo**, procure a lista **Processos Disponíveis** e localize o processo de script ao qual você quer anexar. Você pode identificar processos de script consultando a coluna **Tipo**.  
  
   1.  Se o processo que você quiser depurar estiver sendo executado em outro computador, você primeiro deverá selecionar o computador remoto.
  
   2.  Se o processo estiver sendo executado em uma conta de usuário diferente, marque a caixa de seleção **Mostrar processos de todos os usuários**.  
  
   3.  Se você estiver conectado por meio da **Conexão de Área de Trabalho Remota**, marque a caixa de seleção **Exibir os Processos em Todas as Sessões**.  
  
3. Clique no processo ao qual você quer anexar.  
  
4. No **anexar** caixa, você deverá ver **código do Script** ou **automático: Código do Script**. Se você encontrar algo além disso, siga estas etapas:  
  
   1.  Clique em **Selecionar**.  
  
   2.  Na caixa de diálogo **Selecionar Tipo de Código**, clique em **Depurar estes tipos de código** e selecione **Script**.  
  
   3.  Clique em **OK**.  
  
5. Clique em **Anexar**.  
  
    Neste momento, você pode ver um aviso informando que a depuração de scripts está desabilitada no Internet Explorer. Se isso ocorrer, consulte [Aviso: desabilitado de depuração de Script](../debugger/warning-script-debugging-disabled.md).  
  
   A lista **Processos Disponíveis** é exibida automaticamente quando você abre a caixa de diálogo **Processos**. Os processos podem iniciar e parar em segundo plano quando a caixa de diálogo está aberta. Consequentemente, o conteúdo pode não estar atualizado. Você pode atualizar a lista a qualquer momento para ver a lista atual de processos pressionando o botão **Atualizar**.  
  
   Você pode estar associado a vários programas enquanto depura, mas somente um programa está ativo no depurador em um determinado momento. Você pode definir o programa ativo na barra de ferramentas Local de Depuração. Para obter mais informações, consulte [como: definir o processo atual](/previous-versions/visualstudio/visual-studio-2010/d5d4sxdw(v=vs.100)).  
  
   Todos os comandos de execução no menu **Depurar** afetam o programa ativo. Você pode interromper qualquer programa depurado da caixa de diálogo processos. Ver [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Se você tentar anexar a um processo de propriedade de uma conta de usuário não confiável, aparecerá uma confirmação da caixa de diálogo de aviso de segurança. Para obter mais informações, consulte [aviso de segurança: Anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou, se você não tiver certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
 Em alguns casos, quando você está depurando em uma sessão dos Serviços de Terminal (Área de Trabalho Remota), a lista Processos Disponíveis não exibirá todos os processos disponíveis. Em [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] ou em versões posteriores, se você estiver executando o Visual Studio como um usuário limitado, a lista de Processos Disponíveis não mostrará os processos que estão em execução na sessão 0, usada para serviços e outros processos de servidor, incluindo w3wp.exe. Você pode resolver o problema executando o Visual Studio em uma conta de administrador ou executando o Visual Studio de console do servidor em vez de uma sessão de Terminal Services. Se nenhuma dessas soluções alternativas for possível, uma terceira opção será anexar ao processo digitando vsjitdebugger.exe -p ProcessId na linha de comando do Windows. Você pode determinar o ID do processo usando tlist.exe. Para obter tlist.exe, baixe e instale as Ferramentas de Depuração para o Windows, disponíveis em [Central de Desenvolvedores de Hardware do Windows](/windows-hardware/drivers/dashboard/).  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de script do lado do cliente](../debugger/client-side-script-debugging.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou se você não tiver certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)   
 [Segurança do depurador](../debugger/debugger-security.md)