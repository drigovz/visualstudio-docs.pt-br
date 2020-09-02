---
title: 'Como: usar GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948176"
---
# <a name="how-to-use-getglobalservice"></a>Como usar GetGlobalService
Às vezes, talvez seja necessário obter um serviço de uma janela de ferramentas ou de um contêiner de controle que não tenha sido site, ou que tenha sido site com um provedor de serviços que não saiba sobre o serviço desejado. Por exemplo, talvez você queira gravar no log de atividades de dentro de um controle. Para obter mais informações sobre esses e outros cenários, consulte [como solucionar problemas de serviços](../extensibility/how-to-troubleshoot-services.md).  
  
 Você pode obter a maioria [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dos serviços chamando o <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método estático.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> depende de um provedor de serviços em cache que é inicializado na primeira vez que qualquer VSPackage derivado de é colocado no <xref:Microsoft.VisualStudio.Shell.Package> site. Você deve garantir que essa condição seja atendida ou esteja preparada para um serviço nulo.  
  
 Felizmente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> o funciona corretamente na maioria das vezes.  
  
- Se um VSPackage fornecer um serviço conhecido apenas para outro VSPackage, o VSPackage solicitando o serviço será colocado no local antes que o VSPackage que fornece o serviço seja carregado.  
  
- Se uma janela de ferramenta for criada por um VSPackage, o VSPackage será acessado antes que a janela de ferramentas seja criada.  
  
- Se um contêiner de controle for hospedado por uma janela de ferramenta criada por um VSPackage, o VSPackage será armazenado no site antes do contêiner de controle ser criado.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obter um serviço de dentro de uma janela de ferramentas ou contêiner de controle  
  
- Insira este código no construtor, na janela de ferramentas ou no contêiner de controle:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Esse código obtém um serviço SVsActivityLog e o converte em uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, que pode ser usada para gravar no log de atividades. Para obter um exemplo, consulte [como: usar o log de atividades](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Como: solucionar problemas de serviços](../extensibility/how-to-troubleshoot-services.md)   
 [Usando e fornecendo serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)