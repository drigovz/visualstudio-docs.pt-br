---
title: Como localizar o nome do processo de ASP.NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685959"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Como localizar o nome do processo ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para anexar a um aplicativo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] em execução, você precisará saber o nome do processo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- Se estiver executando o IIS 6.0 ou IIS 7.0, o nome será w3wp.exe.  
  
- Se estiver executando uma versão anterior do IIS, o nome será aspnet_wp.exe.  
  
  Para aplicativos criados usando o [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] ou versões posteriores, o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] código pode residir no sistema de arquivos e ser executado no WebDev.WebServer.exe do servidor de teste. Nesse caso, você deve anexar a WebDev.WebServer.exe em vez do processo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Essa situação aplica-se somente à depuração local.  
  
  Aplicativos ASP antigos são executados dentro do processo inetinfo.exe do IIS quando ele está sendo executado no processo.  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Para determinar se o código de projeto reside no sistema de arquivos ou IIS  
  
1. No Visual Studio, abra **Gerenciador de soluções** se ele ainda não estiver aberto.  
  
2. Selecione o nó superior que contém o nome do aplicativo.  
  
3. Se o título da janela **Propriedades** contiver um caminho de arquivo, o código do aplicativo residirá no sistema de arquivos.  
  
     Caso contrário, o título da janela **Propriedades** conterá o nome do site.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Para determinar a versão do IIS no qual o aplicativo está sendo executado  
  
1. Encontre **Ferramentas administrativas** e execute-as. Dependendo do seu sistema operacional, esse pode ser um ícone dentro do **painel de controle**ou uma entrada de menu que aparece quando você clica em **Iniciar**.  
  
     No Windows XP, o **painel de controle** pode estar no modo de exibição de categoria ou no modo de exibição clássico. No modo de exibição de categoria, você precisa clicar em **alternar para exibição clássica** ou **desempenho e manutenção** para ver o ícone **Ferramentas administrativas** .  
  
2. Em **Ferramentas administrativas**, execute serviços de informações da Internet. Uma caixa de diálogo do MMC é exibida.  
  
3. Se houver mais de um computador listado no painel esquerdo, selecione o computador no qual o código do aplicativo reside.  
  
4. A versão do IIS está na coluna **versão** do painel direito.  
  
## <a name="see-also"></a>Consulte Também  
 [Pré-requisitos para aplicativos Web de depuração remota](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisitos do Sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Preparando para depurar o ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Depurando aplicativos Web e script](../debugger/debugging-web-applications-and-script.md)
