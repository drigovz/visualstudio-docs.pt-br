---
title: Registrando serviços | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 64f2afa6e853978e919e466f91475bed1e8d698c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62971284"
---
# <a name="registering-services"></a>Registrando serviços
Para dar suporte ao carregamento sob demanda, um provedor de serviços deve registrar seus serviços globais com o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Durante o desenvolvimento, os provedores de serviços gerenciados registram serviços e substituições de serviço adicionando atributos ao código-fonte para pacotes e, em seguida, compilando os pacotes no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Isso executa o utilitário RegPkg.exe no assembly resultante, registrando o pacote e preparando-o para implantação. Para obter mais informações, consulte [como registrar um serviço](../misc/how-to-register-a-service.md).  
  
 Os provedores de serviços não gerenciados devem registrar os serviços que eles fornecem com o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na seção de serviços ou a seção de substituições de serviço do registro do sistema. O fragmento de arquivo. reg a seguir mostra como o serviço, SVsTextManager, pode ser registrado:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 No exemplo acima, o número de versão é a versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , como 7,1 ou 8,0, a chave {F5E7E71D-1401-11D1-883B-0000F87579D2} é o identificador de serviço (SID) do serviço, SVsTextManager e o valor padrão {F5E7E720-1401-11D1-883B-0000F87579D2} é o GUID do pacote do VSPackage do Gerenciador de texto, que fornece o serviço.  
  
## <a name="remote-services-and-background-threads"></a>Serviços remotos e threads em segundo plano  
 Os serviços que você fornece não estão automaticamente disponíveis remotamente ou para threads em segundo plano. Para torná-los disponíveis, você deve criar e registrar uma biblioteca de tipos.  
  
 Do código não gerenciado que usa a biblioteca do Visual Studio (VSL), você pode registrar sua biblioteca de tipos dessa maneira:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 No código gerenciado, você pode adicionar uma etapa de pós-compilação como esta:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Usando e fornecendo serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)