---
title: Criando pastas de contêineres-pais para soluções | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709098"
---
# <a name="create-parent-container-folders-for-solutions"></a>Criar pastas de contêiner pai para soluções
Na API Plug-in de controle de origem Versão 1.2, um usuário pode especificar um único destino de controle de origem raiz para todos os projetos da Web dentro da solução. Esta única raiz é chamada de Raiz Super Unificada (SUR).

 Na API Plug-in de controle de origem Versão 1.1, se o usuário adicionasse uma solução de vários projetos ao controle de origem, o usuário seria solicitado a especificar um destino de controle de origem para cada projeto web.

## <a name="new-capability-flags"></a>Novas bandeiras de capacidade
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Novas funções
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE quase sempre cria uma pasta SUR ao adicionar uma solução ao controle de origem. Especificamente, ele faz isso nos seguintes casos:

- O projeto é um projeto web de compartilhamento de arquivos.

- Existem diferentes drives para o projeto e o arquivo de solução.

- Existem diferentes ações para o projeto e o arquivo de solução.

- Os projetos foram adicionados separadamente (em uma solução controlada por origem).

Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], sugere-se que o nome para a pasta SUR seja o mesmo que o nome da solução sem a extensão. A tabela a seguir resume o comportamento nas duas versões.

|Recurso|API plug-in de controle de fonte versão 1.1|API plug-in de controle de fonte versão 1.2|
|-------------| - | - |
|Adicionar solução ao SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Adicionar projeto à solução controlada por origem|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Nota:**  Visual Studio assume que uma solução é uma criança direta do SUR.|

## <a name="examples"></a>Exemplos
 A tabela a seguir lista dois exemplos. Em ambos os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] casos, o usuário é solicitado para um local de destino para a solução sob controle de origem até que o *user_choice* seja especificado como destino. Quando o user_choice é especificado, a solução e dois projetos são adicionados sem solicitar ao usuário destinos de controle de origem.

|Solução contém|Em locais de disco|Estrutura padrão do banco de dados|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Soluções\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Vitória1|*C:\Soluções\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\soluções\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<>/D/web1 de user_choice/<<br /><br /> $/<user_choice>/sln1/win1|

 A pasta SUR e as subpastas são criadas independentemente de a operação ser cancelada ou falhar devido a um erro. Eles não são removidos automaticamente em condições de cancelamento ou erro.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]padrão para o comportamento da versão 1.1 se `SCC_CAP_CREATESUBPROJECT` o `SCC_CAP_GETPARENTPROJECT` plug-in de controle de origem não retornar e sinalizar capacidade. Além disso, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] os usuários podem optar por reverter para o comportamento da Versão 1.1 definindo o valor da seguinte chave para *dword:00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionFolderInSourceSourceControl** = *dword:00000001*

## <a name="see-also"></a>Confira também
- [O que há de novo na API plug-in de controle de fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
