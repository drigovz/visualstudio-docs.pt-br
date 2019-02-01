---
title: VSPerf | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a32de469c5b58ca2bf58901e30b81cfb70ed84b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803521"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use a ferramenta de linha de comando **VsPerf** para:  
  
1. Crie perfil de aplicativos da Windows Store na linha de comando quando o Visual Studio não estiver instalado no dispositivo.  
  
2. Crie perfil de aplicativos de área de trabalho do Windows 8 e aplicativos do Windows Server 2012 usando o método de criação de perfil de amostragem.  
  
   Para obter mais informações sobre opções de criação de perfil, consulte [Ferramentas de desempenho em aplicativos do Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 Este tópico descreve as opções que você pode usar com a ferramenta de linha de comando `vsperf.exe`. Este tópico contém as seguintes seções:  
  
 [Somente aplicativos da Windows Store](#BKMK_windows_store_apps_only)  
  
 [Somente aplicativos da área de trabalho do Windows 8 e do Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Todos os aplicativos](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Somente aplicativos da Windows Store  
 Essas opções aplicam-se apenas a aplicativos da Windows Store.  
  
|||  
|-|-|  
|**/app:{AppName}**|Inicia o criador de perfil e aguarda o lançamento do aplicativo especificado no menu Iniciar.<br /><br /> Execute `vsperf /listapps` para exibir o nome do aplicativo e o PackageFullName de aplicativos instalados.|  
|**/package:{PackageFullName}**|Inicia o criador de perfil e aguarda o lançamento do aplicativo especificado no menu Iniciar.<br /><br /> Execute `vsperf /listapps` para exibir o nome do aplicativo e o PackageFullName de aplicativos instalados.|  
|**/js**|Necessário para aplicativos JavaScript de criação de perfil.<br /><br /> Colete dados de desempenho de aplicativos JavaScript.<br /><br /> Use somente com /package ou /attach.|  
|**/noclr**|Opcional. Não colete dados CLR.<br /><br /> Use somente com /package ou /attach.<br /><br /> Otimização, nenhum símbolo gerenciado será resolvido.|  
|**/listapps**|Lista nomes de aplicativos instalados e PackageFullNames.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Somente aplicativos da área de trabalho do Windows 8 e do Windows Server 2012  
 Essas opções não funcionam em aplicativos da Windows Store.  
  
|||  
|-|-|  
|**/launch:{Executable}**|Inicia e começa a criação de perfil do arquivo executável especificado.|  
|**/args:{ExecutableArguments}**|Especifica os argumentos de linha de comando que passarão o destino **/launch**.|  
|**/console**|Executa o destino **/launch** em uma nova janela de comando.|  
  
##  <a name="BKMK_All_applications"></a> Todos os aplicativos  
 Essas opções aplicam-se a qualquer aplicativo Windows 8 ou o Windows Server 2012.  
  
|||  
|-|-|  
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Coleta dados dos processos especificados.<br /><br /> Use o Gerenciador de Tarefas para exibir a PID (ID do Processo) e processar os nomes dos aplicativos em execução.|  
|**/file:{ReportName}**|Opcional. Especifica o arquivo de saída (substitui o arquivo existente).<br /><br /> Use somente com /package ou /attach.|  
|**/pause**|Pause a coleta de dados.|  
|**/resume**|Retome a coleta de dados.|  
|**/stop**|Pare a coleta de dados e encerre os processos de destino.|  
|**/detach**|Pare a coleta de dados, mas permita que os processos de destino continuem a executar.|  
|**/status**|Mostre status do criador de perfil.|  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de desempenho em aplicativos do Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Criando perfil na linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
