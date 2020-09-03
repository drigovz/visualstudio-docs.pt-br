---
title: Criando pastas de contêiner pai para soluções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196933"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Criando pastas de contêiner pai para soluções
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na API de plug-in de controle do código-fonte versão 1,2, um usuário pode especificar um destino de controle do código-fonte de raiz única para todos os projetos da Web na solução. Essa raiz única é chamada de sur (raiz unificada).  
  
 Na API de plug-in de controle do código-fonte versão 1,1, se o usuário adicionou uma solução multiprojeto ao controle do código-fonte, o usuário foi solicitado a especificar um destino de controle do código-fonte para cada projeto Web.  
  
## <a name="new-capability-flags"></a>Novos sinalizadores de capacidade  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Novas funções  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE quase sempre cria uma pasta sur ao adicionar uma solução ao controle do código-fonte. Especificamente, isso é feito nos seguintes casos:  
  
- O projeto é um projeto Web de compartilhamento de arquivos.  
  
- Há unidades diferentes para o projeto e o arquivo de solução.  
  
- Há diferentes compartilhamentos para o projeto e o arquivo de solução.  
  
- Os projetos foram adicionados separadamente (em uma solução controlada por origem).  
  
  No [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , é recomendável que o nome da pasta sur seja o mesmo que o nome da solução sem a extensão. A tabela a seguir resume o comportamento nas duas versões.  
  
|Recurso|API de plug-in de controle tSource versão 1,1|API de plug-in de controle do código-fonte versão 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Adicionar solução ao SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Adicionar projeto à solução controlada por origem|SccGetProjPath()<br /><br /> OpenProject ()|SccGetParentProjectPath()<br /><br /> SccOpenProject () **Observação:**  o Visual Studio pressupõe que uma solução é um filho direto do sur.|  
  
## <a name="examples"></a>Exemplos  
 A tabela a seguir lista dois exemplos. Em ambos os casos, o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usuário será solicitado a fornecer um local de destino para a solução no controle do código-fonte até que a  *user_choice* seja especificada como um destino. Quando o user_choice é especificado, a solução e dois projetos são adicionados sem solicitar ao usuário destinos de controle do código-fonte.  
  
|A solução contém|Em locais de disco|Estrutura padrão do banco de dados|  
|-----------------------|-----------------------|--------------------------------|  
|sln1. sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot $ \web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*/C/web1<br /><br /> $/*user_choice*/web2|  
|sln1. sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*/D/web1<br /><br /> $/*user_choice*/sln1/win1|  
  
 A pasta SUR e as subpastas são criadas independentemente de a operação ser cancelada ou falhar devido a um erro. Elas não são removidas automaticamente em condições de cancelamento ou erro.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o padrão é o comportamento da versão 1,1 se o plug-in de controle do código-fonte não retornar `SCC_CAP_CREATESUBPROJECT` e os `SCC_CAP_GETPARENTPROJECT` sinalizadores de funcionalidade. Além disso, os usuários de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podem optar por reverter para o comportamento da versão 1,1 definindo o valor da seguinte chave como DWORD: 00000001:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Consulte Também  
 [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
