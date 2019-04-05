---
title: 'Erro: Falha no Logon remoto do grupo de trabalho | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0157b18c0b0dfce2ba69482dc1c61e1ddf3a996
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928136"
---
# <a name="error-workgroup-remote-logon-failure"></a>Erro: Falha de logon remoto do grupo de trabalho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este erro é:  
  
 Falha de logon: usuário desconhecido ou senha inválida  
  
 **Causa**  
  
 Esse erro pode ocorrer quando você está depurando de um computador em um grupo de trabalho e tentar se conectar ao computador remoto. Possíveis causas incluem:  
  
-   Não há nenhuma conta com o nome e a senha correspondentes no computador remoto.  
  
-   Se o computador do Visual Studio e o computador remoto estiverem em grupos de trabalho, esse erro poderá ocorrer devido à configuração padrão de **Política de Segurança Local** no computador remoto. A configuração padrão de **Política de Segurança Local** é **Convidado somente – os usuários locais são autenticados como Convidado**. Para depurar nessa configuração, você deverá alterar a configuração no computador remoto para **Clássico – os usuários locais são autenticados como eles próprios**.  
  
> [!NOTE]
>  Você deve ser administrador para realizar as seguintes tarefas.  
  
### <a name="to-open-the-local-security-policy-window"></a>Para abrir a janela Política de Segurança Local  
  
1.  Inicie o snap-in **secpol.msc** do snap-in Console de Gerenciamento Microsoft. Digite secpol.msc na pesquisa do Windows, na caixa de execução do Windows ou em um prompt de comando.  
  
### <a name="to-add-user-rights-assignments"></a>Para adicionar atribuições de direitos de usuário  
  
1.  Abra o local  
  
2.  Abra a janela **Política de Segurança Local**.  
  
3.  Expanda a pasta **Políticas Locais**.  
  
4.  Clique em **Atribuição de Direitos do Usuário**.  
  
5.  Na coluna **Política**, clique duas vezes em **Depurar programas** para exibir as atribuições locais atual da política de grupo na caixa de diálogo **Configuração de Política de Segurança Local**.  
  
     ![Direitos de usuário de política de segurança local](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Para adicionar novos usuários, clique no botão **Adicionar Usuário ou Grupo**.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Para alterar o Modelo de Compartilhamento e Segurança  
  
1.  Abra a janela **Política de Segurança Local**.  
  
2.  Expanda a pasta **Políticas Locais**.  
  
3.  Clique em **Opções de Segurança**.  
  
4.  No **diretiva** coluna, clique duas vezes em **acesso à rede: Modelo de compartilhamento e segurança para contas locais**.  
  
5.  No **acesso à rede: Modelo de compartilhamento e segurança para contas locais** caixa de diálogo, altere o valor a ser **Clássico - os usuários locais são autenticados como eles próprios** e clique no **aplicar** botão.  
  
     ![Opções de segurança da política de segurança local](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas e erros de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)
