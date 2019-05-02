---
title: 'Como: Usar o Log de atividades | Microsoft Docs'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432570"
---
# <a name="how-to-use-the-activity-log"></a>Como: Usar o log de atividades
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os VSPackages pode gravar mensagens no log de atividade. Esse recurso é especialmente útil para depurar os VSPackages em ambientes de varejo.  
  
> [!TIP]
> O log de atividades está sempre ativado. O Visual Studio manterá um buffer progressivo de entradas de cem pela última vez, bem como as dez primeiras entradas, o que tem informações de configuração geral.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Para gravar uma entrada ao log de atividades  
  
1. Inserir este código no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método ou em qualquer outro método, exceto no construtor de VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Esse código obtém os <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de serviço e a converte para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> grava uma entrada informativa no log de atividades usando o contexto cultural atual.  
  
2. Quando o VSPackage é carregado (normalmente, quando um comando é invocado ou uma janela é aberta), o texto é escrito para o log de atividades.  
  
### <a name="to-examine-the-activity-log"></a>Para examinar o log de atividades  
  
1. Localizar o log de atividades na subpasta para dados do Visual Studio: *% AppData %* \Microsoft\VisualStudio\14.0\ActivityLog.XML...  
  
2. Abra o log de atividades com qualquer editor de texto. Aqui está uma entrada típica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Como o log de atividades é um serviço, o log de atividades não está disponível no construtor de VSPackage.  
  
 Você deve obter o log de atividades antes de gravar. Não armazenar em cache ou salvar o log de atividades para uso futuro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Solucionar problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
