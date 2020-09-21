---
title: Como registrar um serviço | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838313"
---
# <a name="how-to-register-a-service"></a>Como registrar retornos de chamada
A MPF (estrutura de pacote gerenciada) fornece atributos para controlar o registro de serviços gerenciados. O utilitário RegPkg usa esses atributos para registrar um serviço com o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="example"></a>Exemplo  
 O código a seguir é de [exemplos de VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 O <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registra o serviço SMyGlobalService com [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para obter mais informações <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> sobre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> o e [o, consulte Registrando e cancelando o registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Para registrar um serviço que substitui outro serviço com o mesmo nome, use o <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> em vez do <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .  
  
## <a name="robust-programming"></a>Programação robusta  
 Para facilitar a recompilação de um provedor de serviços sem alterar o cliente de serviço, ou vice-versa, você pode definir o serviço e suas interfaces em um módulo de assembly separado. O código a seguir é do arquivo IMyGlobalService.cs no exemplo Reference. Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 O <xref:System.Runtime.InteropServices.ComVisibleAttribute> é necessário para obter a interface do código não gerenciado.  
  
> [!NOTE]
> Embora você possa usar o mesmo tipo ou GUID para o serviço e a interface, é recomendável separar os dois porque um serviço pode expor interfaces diferentes.  
  
## <a name="see-also"></a>Consulte Também  
 [Registrando VSPackages](../extensibility/internals/registering-vspackages.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)