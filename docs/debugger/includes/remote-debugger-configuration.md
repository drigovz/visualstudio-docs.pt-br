---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043457"
---
1. No computador remoto, localizar e iniciar o **depurador remoto** da **iniciar** menu. 
   
   Se você não tiver permissões administrativas no computador remoto, clique com botão direito do **depurador remoto** aplicativo e selecione **executar como administrador**. Caso contrário, apenas iniciá-lo normalmente.

   Se você estiver planejando anexar a um processo que está sendo executado como um administrador ou está em execução em um usuário diferente da conta (como o IIS), clique com botão direito do **depurador remoto** aplicativo e selecione **executar como administrador**. Para obter mais informações, consulte [executar o depurador remoto como um administrador](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. Na primeira vez que você inicia o depurador remoto (ou antes você tiver configurado), o **configuração de depuração remota** caixa de diálogo é exibida.  
  
    ![Configuração do depurador remoto](../media/remotedebuggerconfwizardpage.png "configuração do depurador remoto")  
  
1. Se a API de serviços de Web do Windows não estiver instalada, o que ocorre apenas no Windows Server 2008 R2, selecione a **instalar** botão.  
  
1. Selecione pelo menos um tipo de rede que deseja usar as ferramentas remotas no. Se os computadores estiverem conectados por meio de um domínio, você deve escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo de trabalho ou um grupo doméstico, escolha o item de segundo ou terceiro conforme apropriado.  
  
1. Selecione **configurar a depuração remota** para configurar o firewall e iniciar o depurador remoto.  
  
1. Quando a configuração for concluída, o **depurador remoto** janela é exibida.
  
    ![Janela de depurador remoto](../media/remotedebuggerwindow.png "janela do depurador remoto")
  
    O depurador remoto agora está aguardando uma conexão. Use o nome do servidor e porta número mostrado para definir a configuração de conexão remota no Visual Studio.  
  
Para interromper o depurador remoto, selecione **arquivo** > **Exit**. Você pode reiniciá-lo partir o **iniciar** menu, ou da linha de comando:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
