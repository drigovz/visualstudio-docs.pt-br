---
title: Não é possível anexar ao processo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c74799daf57ca031c4b3ce6bf76f72e453eeb0b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838644"
---
# <a name="unable-to-attach-to-the-process"></a>Não é possível anexar ao processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Não é possível anexar ao processo. O componente do depurador no servidor recebeu acesso negado ao se conectar a esse computador.  
  
 Há dois cenários comuns que causam esse erro:  
  
 **Cenário 1:** o computador A executa o Windows XP. O computador B executa o Windows Server 2003. O registro no computador B contém o seguinte valor DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 O usuário 1 inicia uma sessão do Terminal Server (sessão 1) no computador B e inicia um aplicativo gerenciado a partir dessa sessão.  
  
 O usuário 2, que é o administrador em ambos os computadores, está conectado no computador A. A partir daí, ele tentará anexar a um aplicativo em execução na sessão 1 no computador B.  
  
 **Cenário 2:** um usuário fez o logon em dois computadores, A e B, do mesmo grupo de trabalho, usando a mesma senha em ambos os computadores. O depurador está em execução no computador A e tentando se conectar a um aplicativo gerenciado em execução no computador B. A máquina A tem **acesso à rede: modelo de compartilhamento e segurança para contas locais** definidas como **convidado**.  
  
### <a name="to-solve-scenario-1"></a>Para solucionar o cenário 1  
  
- Execute o depurador e o aplicativo gerenciado no mesmo nome e senha da conta do usuário.  
  
### <a name="to-solve-scenario-2"></a>Para solucionar o cenário 2  
  
1. No menu **Iniciar**, selecione **Painel de Controle**.  
  
2. No painel de controle, clique duas vezes em **Ferramentas administrativas**.  
  
3. Na janela ferramentas administrativas, clique duas vezes em **política de segurança local**.  
  
4. Na janela Política de Segurança Local, selecione **Políticas Locais**.  
  
5. Na coluna **Políticas**, clique duas vezes em **Acesso à rede: modelo de compartilhamento e segurança para contas locais**.  
  
6. Na caixa de diálogo **Acesso à rede: modelo de compartilhamento e segurança para contas locais**, altere a configuração de segurança local para **Clássico** e clique em **OK**.  
  
    > [!CAUTION]
    > A alteração do modelo de segurança para Clássico pode resultar em acesso inesperado a arquivos e componentes DCOM compartilhados. Se você fizer essa alteração, um usuário remoto poderá ser autenticado com sua conta de usuário local em vez como Convidado. Se um usuário remoto corresponder ao seu nome de usuário e senha, esse usuário poderá acessar qualquer pasta ou objeto DCOM que você compartilhou. Se você usar esse modelo de segurança, certifique-se de que todas as contas de usuário no computador tenham senhas fortes ou configurem uma ilha de rede isolada para a depuração e computadores depurados para impedir o acesso não autorizado.  
  
7. Feche todas as janelas.  
  
## <a name="see-also"></a>Consulte Também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)
