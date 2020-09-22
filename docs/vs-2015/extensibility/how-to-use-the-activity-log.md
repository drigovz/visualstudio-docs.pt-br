---
title: 'Como: usar o log de atividades | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838641"
---
# <a name="how-to-use-the-activity-log"></a>Como usar o log de atividades
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages pode gravar mensagens no log de atividades. Esse recurso é especialmente útil para depurar VSPackages em ambientes de varejo.  
  
> [!TIP]
> O log de atividades está sempre ativado. O Visual Studio mantém um buffer contínuo das últimas 100 entradas, bem como as dez primeiras entradas, que têm informações gerais de configuração.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Para gravar uma entrada no log de atividades  
  
1. Insira esse código no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método ou em qualquer outro método, exceto o Construtor VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Esse código obtém o <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> serviço e o converte em uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> grava uma entrada informativa no log de atividades usando o contexto cultural atual.  
  
2. Quando o VSPackage é carregado (geralmente quando um comando é invocado ou uma janela é aberta), o texto é gravado no log de atividades.  
  
### <a name="to-examine-the-activity-log"></a>Para examinar o log de atividades  
  
1. Localize o log de atividades na subpasta para dados do Visual Studio: *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML..  
  
2. Abra o log de atividades com qualquer editor de texto. Aqui está uma entrada típica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Como o log de atividades é um serviço, o log de atividades fica indisponível no Construtor VSPackage.  
  
 Você deve obter o log de atividades logo antes de gravar nele. Não armazene em cache ou salve o log de atividades para uso futuro.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Solução de problemas do VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
