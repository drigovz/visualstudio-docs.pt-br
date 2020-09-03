---
title: Eventos (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d24fc7a01a8eebe356f37704c1a821332f5dca1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850758"
---
# <a name="events-vsperfcmd"></a>Eventos (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A opção **Eventos** do VSPerfCmd.exe controla o registro em log do ETW (Rastreamento de Eventos para Windows). Os dados ETW são salvos em um arquivo .etl separado do arquivo de dados do criador de perfil. Os dados podem ser exibidos em um relatório usando o comando [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.  
  
 A opção **Eventos** pode ser chamada a qualquer momento antes do comando **Shutdown** do VSPerfCmd ser chamado para interromper a criação de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 **On**&#124;**Off**  
 Inicia ou interrompe a coleta de dados de evento.  
  
 `Guid`  
 O GUID do controle de provedor.  
  
 `ProviderName`  
 O nome do provedor que está registrado com o WMI (Instrumentação de Gerenciamento do Windows).  
  
 `Flags`  
 Um valor de sinalizadores hexadecimais prefixados com "0x" que é definido pelo provedor de eventos.  
  
 `Level`  
 Especifica o volume de dados coletado. `Level` é definido pelo provedor de eventos.  
  
 A opção **Eventos** compreende as seguintes palavras-chave kernel como nomes de provedor:  
  
 **Processo**  
 Processar eventos  
  
 **Processo**  
 Eventos de threads  
  
 **Imagem**  
 Eventos de carregamento e descarregamento de imagens  
  
 **Disco**  
 Eventos de E/S de disco  
  
 **Arquivo**  
 Eventos de E/S de arquivo  
  
 **Hardfault**  
 Falhas de páginas físicas  
  
 **Pagefault**  
 Falhas de páginas lógicas  
  
 **Rede**  
 Eventos de rede  
  
 **Registro**  
 Eventos de acesso ao Registro  
  
 Observe que o Kernel Provider só pode ser habilitado. Ele não pode ser desabilitado, nem seus sinalizadores podem ser modificados, até que o monitor seja desligado.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Quando eventos CLR ETW estiverem habilitados, os dados de inicialização adicional também serão coletados no relatório de Exibição de Rastreamento. Para excluir eventos de inicialização daqueles que aparecem no relatório, use o seguinte comando:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> Se você não excluir os eventos de inicialização, como tais eventos não são listados no arquivo MOF (Managed Object Format), eles aparecerão como GUIDs no relatório. Para obter mais informações, consulte esta página no site da Microsoft: [arquivo de Managed Object Format de exemplo (MOF)](https://msdn.microsoft.com/library/default.aspx).  
  
## <a name="see-also"></a>Consulte Também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criação de perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criação de perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
