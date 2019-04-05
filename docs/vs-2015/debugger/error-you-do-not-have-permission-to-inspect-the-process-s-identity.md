---
title: 'Erro: Você não tem permissão para inspecionar o processo de&#39;identidade de s | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f173be87987cbc8bcfb3390dfdaaf5eab7501bb6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925549"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Erro: Você não tem permissão para inspecionar o processo de&#39;identidade de s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você não tem permissão para inspecionar a identidade do processo. Isto pode ocorrer devido à configuração do sistema.  
  
 O depurador não pôde inspecionar a identidade do processo, que são informações necessárias para depuração. A causa mais provável é que os Serviços de Terminal estão sendo desabilitados. O serviço dos Serviços de Terminal é habilitado por padrão. Siga estas etapas para habilitá-lo novamente.  
  
### <a name="to-enable-terminal-services"></a>Para habilitar Serviços de Terminal  
  
1.  Clique em **Iniciar** e escolha **Painel de Controle**.  
  
2.  No Painel de Controle, escolha **Alternar para o Modo de Exibição Clássico** se necessário e clique duas vezes em **Ferramentas Administrativas**.  
  
3.  Na janela **Ferramentas Administrativas**, clique duas vezes em **Gerenciamento de Computador**.  
  
4.  Na janela Gerenciamento de Computador, expanda o nó **Serviços e Aplicativos**.  
  
5.  Em **Serviços e Aplicativos**, clique em **Serviços**.  
  
     Uma lista de serviços aparece no painel direito.  
  
6.  Na lista **Serviços**, clique com o botão direito do mouse em **Serviços de Terminal** e escolha **Propriedades**.  
  
7.  No **propriedades de serviços de Terminal** janela, vá para o **gerais** guia e defina **tipo de inicialização** para **Manual**.  
  
8.  Clique em **OK**.  
  
9. Reinicie o computador.  
  
     Esse procedimento não habilita automaticamente a Área de Trabalho Remota. Se quiser habilitar a Área de Trabalho Remota no computador, execute o seguinte procedimento adicional.  
  
### <a name="to-enable-remote-desktop"></a>Para habilitar a Área de Trabalho Remota  
  
1.  Clique em **Iniciar** e clique com o botão direito do mouse em **Meu Computador**.  
  
2.  Escolha **Propriedades**.  
  
     A janela **Propriedades do Sistema** é exibida.  
  
3.  Clique em **Remoto**.  
  
4.  Em **Área de Trabalho Remota**, selecione **Permitir que usuários se conectem remotamente a este computador**.  
  
5.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)
