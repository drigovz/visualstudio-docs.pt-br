---
title: Escolhendo entre VSPackages compartilhado e com controle de versão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821975"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Escolhendo entre VSPackages compartilhados e com controle de versão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Versões diferentes do Visual Studio podem coexistir no mesmo computador. O VSPackages pode dar suporte a qualquer combinação de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versões.  
  
 Você pode habilitar instalações lado a lado do VSPackages por meio de uma das duas estratégias, a estratégia compartilhada ou a estratégia com controle de versão. Ambos acomodam a presença de várias versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e de versões associadas do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Na estratégia compartilhada, um VSPackage é registrado para uso em várias versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Na estratégia com versão, várias DLLs VSPackage são instaladas, uma para cada versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à qual você dá suporte.  
  
## <a name="shared-vspackages"></a>VSPackages compartilhado  
 Usar um VSPackage compartilhado é apropriado quando você usa o mesmo VSPackage em várias versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para implementar um VSPackage compartilhado, você deve executar as seguintes etapas:  
  
- Torne seu VSPackage compatível com várias versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Duas maneiras de fazer isso estão disponíveis:  
  
  - Limite seu VSPackage a usar apenas os recursos da versão mais antiga do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que você dá suporte.  

  - Programe seu VSPackage para adaptar-se à versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] em que está em execução. Em seguida, se as consultas para serviços mais recentes falharem, seu VSPackage poderá oferecer outros serviços com suporte em versões mais antigas do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Registre seu VSPackage adequadamente. Para obter mais informações, consulte [registro de VSPackage](../extensibility/internals/vspackage-registration.md) e [registro VSPackage gerenciado](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Registre as extensões de arquivo adequadamente. Para obter mais informações, consulte [registrando extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Crie um instalador que implanta seu VSPackage para as versões apropriadas do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para obter mais informações, consulte [instalando o VSPackages com Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [Gerenciamento de componentes](../extensibility/internals/component-management.md).  
  
- Resolva o problema de colisões de registro. Para obter mais informações, consulte [VSPackage Registration](../extensibility/internals/vspackage-registration.md).  
  
- Verifique se os arquivos compartilhados e com controle de versão respeitam a contagem de referência para permitir a instalação e remoção segura de várias versões. Para obter mais informações, consulte [Gerenciamento de componentes](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages com controle de versão  
 Sob a estratégia de VSPackage com controle de versão, você cria um VSPackage para cada versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] com suporte. Fazer isso é apropriado quando você espera aproveitar os serviços fornecidos pelas versões posteriores do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , pois cada VSPackage pode evoluir sem afetar os outros. No entanto, a estratégia com controle de versão da criação de vários binários, seja de uma única base de código ou de várias bases de código independentes, pode envolver mais desenvolvimento inicial do que a estratégia compartilhada. Além disso, o trabalho de configuração adicional pode ser necessário porque você deve criar uma configuração separada para cada versão ou uma única configuração que detecta as versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instaladas e que o VSPackage dá suporte.  
  
## <a name="binary-compatibility"></a>Compatibilidade binária  
 Geralmente, a compatibilidade binária permite que VSPackages de código nativo desenvolvidos com versões anteriores do Visual Studio sejam executadas em versões posteriores do Visual Studio. No entanto, há três exceções importantes:  
  
- Se o seu VSPackage se basear em uma versão específica do Common Language Runtime, ele deverá determinar em qual versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] está sendo executada.  
  
- Um VSPackage pode ter uma dependência em um recurso específico de outro VSPackage ou outro produto. Consequentemente, o VSPackage pode executar apenas onde a dependência é satisfeita.  
  
- Um VSPackage pode ser afetado por uma correção de segurança em uma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Service Pack ou em uma versão posterior do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Nesses casos, um VSPackage desenvolvido com uma versão anterior do [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] pode não ser executado em versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] após a aplicação da correção de segurança. No entanto, você pode recompilar seu pacote com a versão mais recente e fazer com que ele também seja executado em versões anteriores.  
  
  O VSPackages gerenciado deve ser criado usando uma versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e o [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] que corresponde à versão de destino do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  Além de planejar a compatibilidade binária para seus binários do VSPackage, você também deve considerar os formatos de arquivo da solução e do projeto. Se o seu VSPackage cria um novo tipo de projeto, você deve decidir se ele pode ser executado em apenas uma versão ou em várias versões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para obter mais informações, consulte [upgrading Custom Projects](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Instalando o VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gerenciamento de componentes](../extensibility/internals/component-management.md)
