---
title: Não é possível anexar ao processo | Microsoft Docs
description: Aprenda o significado de "não é possível anexar ao processo", os dois cenários que causam isso e as soluções.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e7a90d2e08d16ddfb7ac22baafe58cf76b4895d3
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150841"
---
# <a name="unable-to-attach-to-the-process"></a>Não é possível anexar ao processo
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

## <a name="see-also"></a>Confira também
- [Configurações e preparação do depurador](../debugger/debugger-settings-and-preparation.md)