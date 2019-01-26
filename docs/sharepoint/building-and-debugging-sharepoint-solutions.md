---
title: Compilando e depurando soluções do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1cdcf71821bd0f7e9739bc194834500c2dfc6fd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871553"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Compilar e depurar soluções do SharePoint
  Em geral, compilando e depurando soluções do SharePoint é o mesmo que a compilação e depuração de outros tipos de projetos em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Os tópicos nesta seção explicam as diferenças que existem.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Saída do projeto para soluções do SharePoint
 Criação de soluções do SharePoint cria assemblies e um pacote de solução (*. wsp*) arquivos. A tabela a seguir mostra os locais desses arquivos durante uma compilação.  
  
|Criar item|Pasta de saída|  
|----------------|-------------------|  
|Assembly, o banco de dados do programa (*. PDB*), e *wsp* arquivos.|*\<ProjectName > \bin\debug* ou  *\<ProjectName > \bin\Release.*|  
|Arquivos de item de projeto do SharePoint.|*\<ProjectName > \pkg\debug* ou  *\<ProjectName > \pkg\release*|  
|Crie arquivos intermediários.|*\<ProjectName > \obj\debug* ou  *\<ProjectName > \obj\release*|  
|Arquivos intermediários do pacote.|*\<ProjectName > \pkgobj\debug* ou  *\<ProjectName > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Criar soluções do SharePoint
 Para criar soluções do SharePoint, o computador de desenvolvimento deve ter a versão correta do SharePoint server instalado. Caso contrário, a criação de soluções do SharePoint é o mesmo que compilar outros tipos de projetos em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, confira [Como: Criar soluções do SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Depurar e testar soluções do SharePoint
 Antes de depurar, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia o *. wsp* pacote ao servidor do SharePoint, ativa o Site e os recursos no escopo da Web e, em alguns casos, inicia o projeto. Em outros casos, talvez você precise abrir o projeto manualmente. Para obter mais informações, consulte [soluções do SharePoint solucionar](../sharepoint/troubleshooting-sharepoint-solutions.md) e [soluções do SharePoint depurar](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Depurar e verifique se a soluções do SharePoint usando recursos de serviços de DevOps do Azure
 Recursos de serviços de DevOps do Azure, como testes de unidade e o IntelliTrace permitem que você mais precisa identificar problemas em suas soluções do SharePoint. Criação de perfil permite que você localizar e identificar áreas de problema de desempenho em suas soluções do SharePoint. Para obter mais informações, consulte [Verificando e depurando código do SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) e [criação de perfil de desempenho de aplicativos do SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Segurança durante o processo de compilação
 Para empacotar ou implantar soluções do SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] deve ter permissão para copiar arquivos para o servidor do SharePoint. Você deve executar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como um processo elevado e seu usuário de conta deve ser um administrador de coleções de sites no servidor do SharePoint. Além disso, você deve especificar se o seu projeto é uma solução em área restrita ou uma solução de farm. Para obter mais informações, consulte [diferenças entre em modo seguro e soluções de Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Usando o comando limpo  
 Quando uma solução do SharePoint é instalada em um servidor do SharePoint para depuração, o **Clean** comando não desinstalar a solução. Em vez disso, você deve desativar os recursos por meio da configuração do SharePoint.  
  
## <a name="see-also"></a>Consulte também
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Procurar conexões do SharePoint usando o Gerenciador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
