---
title: Não é possível anexar ao processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47fb4084e54915e44e79c3da2e50a418d2d8cc39
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693172"
---
# <a name="unable-to-attach-to-the-process"></a>Não é possível anexar ao processo
Não é possível anexar ao processo. O componente do depurador no servidor recebeu acesso negado ao se conectar a esse computador.

 Há dois cenários comuns que causam esse erro:

 **Cenário 1:** o computador A executa o Windows XP. O computador B executa o Windows Server 2003. O registro no computador B contém o seguinte valor DWORD:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 O usuário 1 inicia uma sessão do Terminal Server (sessão 1) no computador B e inicia um aplicativo gerenciado a partir dessa sessão.

 Usuário 2, que é o administrador em ambos os computadores, é registrado no computador A. A partir daí, ele tenta se anexar a um aplicativo em execução na sessão 1 no computador B.

 **Cenário 2:** um usuário fez o logon em dois computadores, A e B, do mesmo grupo de trabalho, usando a mesma senha em ambos os computadores. O depurador está em execução na máquina e tentando se conectar a um aplicativo gerenciado em execução no computador do computador B. A tem **acesso à rede: modelo de compartilhamento e segurança para contas locais** definido como **convidado**.

### <a name="to-solve-scenario-1"></a>Para solucionar o cenário 1

-   Execute o depurador e o aplicativo gerenciado no mesmo nome e senha da conta do usuário.

### <a name="to-solve-scenario-2"></a>Para solucionar o cenário 2

1.  No menu **Iniciar**, selecione **Painel de Controle**.

2.  No Painel de Controle, clique duas vezes em **Ferramentas administrativas**.

3.  Na janela Ferramentas administrativas, clique duas vezes em **Política de Segurança Local**.

4.  Na janela Política de Segurança Local, selecione **Políticas Locais**.

5.  Na coluna **Políticas**, clique duas vezes em **Acesso à rede: modelo de compartilhamento e segurança para contas locais**.

6.  Na caixa de diálogo **Acesso à rede: modelo de compartilhamento e segurança para contas locais**, altere a configuração de segurança local para **Clássico** e clique em **OK**.

    > [!CAUTION]
    >  A alteração do modelo de segurança para Clássico pode resultar em acesso inesperado a arquivos e componentes DCOM compartilhados. Se você fizer essa alteração, um usuário remoto poderá ser autenticado com sua conta de usuário local em vez como Convidado. Se um usuário remoto corresponder ao seu nome de usuário e sua senha, esse usuário terá acesso a qualquer pasta ou objeto DCOM você compartilhar. Se você usar esse modelo de segurança, verifique se todas as contas de usuário no computador têm senhas fortes ou configure uma ilha isolada de rede para os computadores de depuração e depurados para impedir o acesso não autorizado.

7.  Feche todas as janelas.

## <a name="see-also"></a>Consulte também
- [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)