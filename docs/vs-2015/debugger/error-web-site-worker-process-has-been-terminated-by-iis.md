---
title: 'Erro: Processo de trabalho do site da Web foi encerrado pelo IIS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97b6b7a798483000916ee8c99a8000fd45b9cc00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929410"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Erro: O processo de trabalho do site foi terminado pelo IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O depurador interrompeu a execução de código no site. Isso fez o IIS (Serviços de Informações da Internet) supor que o processo de trabalho parou de responder. Consequentemente, o IIS terminou o processo de trabalho.  
  
 Para retomar a depuração, será necessário configurar o IIS para permitir que o processo de trabalho continue. Essa mensagem de erro não aparece em versões do IIS que são anteriores ao IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Para configurar o IIS 7 para permitir que o processo de trabalho continue  
  
1. Abra a janela **Ferramentas Administrativas**.  
  
   1.  Clique em **Iniciar** e escolha **Painel de Controle**.  
  
   2.  No **Painel de Controle**, escolha **Alternar para o Modo de Exibição Clássico** se necessário e clique duas vezes em **Ferramentas Administrativas**.  
  
2. Na janela **Ferramentas Administrativas**, clique duas vezes em **Serviços de Informações da Internet (IIS)**.  
  
    O Gerenciador do IIS é aberto.  
  
3. No painel **Conexões**, expanda o nó \<nome do computador> se necessário.  
  
4. No nó \<nome do computador>, clique em **Pools de Aplicativos**.  
  
5. Na lista **Pools de Aplicativos**, clique com o botão direito do mouse no nome do pool no qual seu aplicativo está sendo executado e clique em **Configurações Avançadas**.  
  
6. Na caixa de diálogo **Configurações Avançadas**, localize a seção **Modelo de Processo** e execute uma das seguintes ações:  
  
   - Defina **Ping Habilitado** como **False**.  
  
   - Defina **Tempo de Resposta Máximo de Ping** com um valor maior do que 90 segundos.  
  
     Configurar **Ping Habilitado** como **False** impede que o IIS verifique se o processo de trabalho ainda está em execução e mantém o processo de trabalho ativo até que você pare o processo depurado. Configurar **Tempo de Resposta Máximo de Ping** com um valor grande permite que o IIS continue monitorando o processo de trabalho.  
  
7. Clique em **OK** para fechar a caixa de diálogo **Configurações Avançadas**.  
  
8. Feche o Gerenciador do IIS e a janela **Ferramentas Administrativas**.  
  
## <a name="see-also"></a>Consulte também  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)
