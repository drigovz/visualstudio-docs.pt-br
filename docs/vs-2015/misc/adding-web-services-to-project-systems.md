---
title: Adicionando serviços Web a sistemas de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002656"
---
# <a name="adding-web-services-to-project-systems"></a>Adição de serviços Web para sistemas de projeto
Os serviços Web XML são, em geral, recursos endereçáveis de URL que retornam informações programáticas para o sistema do projeto usando o protocolo SOAP (Simple Object Access Protocol). Você pode integrar os serviços Web ao sistema de projeto VSPackage usando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interface.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Para adicionar um serviço Web ao sistema de projeto  
  
1. Chame `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> a interface por meio do <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> serviço.  
  
2. Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> . Se você passar `pDiscoverySession` o parâmetro como `NULL` , uma sessão de descoberta será criada para você e a sessão será armazenada em cache para que fique disponível para uso subsequente pela <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> o método retorna um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> . Passe o objeto Automation para a pasta referências do serviço Web como o `pUnkWebReferenceFolder` parâmetro. O ambiente do Visual Studio verifica se o serviço Web já está presente. Se o serviço Web não estiver presente, o ambiente baixará e adicionará o serviço Web a uma pasta e a arquivos adicionais (como arquivos. WSDL) aos nós filho da pasta.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>