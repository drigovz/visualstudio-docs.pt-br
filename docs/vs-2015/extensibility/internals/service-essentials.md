---
title: Service Essentials | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696074"
---
# <a name="service-essentials"></a>Conceitos básicos do serviço
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um serviço é um contrato entre duas VSPackages. Um VSPackage fornece um conjunto específico de interfaces para que outro VSPackage consuma. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] é, em si, uma coleção de VSPackages que fornece serviços para outros VSPackages.  
  
 Por exemplo, você pode usar o serviço SVsActivityLog para obter uma interface IVsActivityLog, que pode ser usada para gravar no log de atividades. Para obter mais informações, consulte [como: usar o log de atividades](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] também fornece alguns serviços internos que não estão registrados. O VSPackages pode substituir serviços internos ou outros fornecendo uma substituição de serviço. Somente uma substituição de serviço é permitida para qualquer serviço.  
  
 Os serviços não têm capacidade de descoberta. Portanto, você deve saber o identificador de serviço (SID) de um serviço que deseja consumir e deve saber quais interfaces ele fornece. A documentação de referência para o serviço fornece essas informações.  
  
- VSPackages que fornecem serviços são chamados de provedores de serviços.  
  
- Os serviços que são fornecidos a outros VSPackages são chamados de serviços globais.  
  
- Os serviços que estão disponíveis somente para o VSPackage que os implementa, ou para qualquer objeto que ele cria, são chamados de serviços locais.  
  
- Os serviços que substituem serviços internos ou serviços fornecidos por outros pacotes são chamados de substituições de serviço.  
  
- Serviços, ou substituições de serviço, são carregados sob demanda, ou seja, o provedor de serviços é carregado quando o serviço que ele fornece é solicitado por outro VSPackage.  
  
- Para dar suporte ao carregamento sob demanda, um provedor de serviços registra seus serviços globais com o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Para obter mais informações, consulte [registrando serviços](../../misc/registering-services.md).  
  
- Depois de obter um serviço, use [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (código não gerenciado) ou conversão (código gerenciado) para obter a interface desejada, por exemplo:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- O código gerenciado refere-se a um serviço por seu tipo, enquanto o código não gerenciado se refere a um serviço por seu GUID.  
  
- Quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o carrega um VSPackage, ele passa um provedor de serviços para o VSPackage para conceder o VSPackage acesso aos serviços globais. Isso é chamado de "Localizando" do VSPackage.  
  
- VSPackages podem ser provedores de serviços para os objetos que criam. Por exemplo, um formulário pode enviar uma solicitação de um serviço de cores para seu quadro, que pode passar a solicitação para [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Os objetos gerenciados que estão profundamente aninhados, ou não site, podem chamar o <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> acesso direto aos serviços globais. Para obter mais informações, consulte [como: usar GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Lista de serviços disponíveis](../../extensibility/internals/list-of-available-services.md)   
 [Usando e fornecendo serviços](../../extensibility/using-and-providing-services.md)   
 [Conversão e conversões de tipo](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Transmissão](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
