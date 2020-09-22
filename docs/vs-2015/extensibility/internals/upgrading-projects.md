---
title: Atualizando projetos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838327"
---
# <a name="upgrading-projects"></a>Atualizando projetos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As alterações no modelo de projeto de uma versão do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para a próxima podem exigir que projetos e soluções sejam atualizados para que possam ser executados na versão mais recente. O [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] fornece interfaces que podem ser usadas para implementar o suporte de atualização em seus próprios projetos.  
  
## <a name="upgrade-strategies"></a>Estratégias de atualização  
 Para dar suporte a uma atualização, a implementação do sistema do projeto deve definir e implementar uma estratégia de atualização. Para determinar sua estratégia, você pode optar por dar suporte a backups lado a lado (SxS), copiar backup ou ambos.  
  
- Backup SxS significa que um projeto copia apenas os arquivos que precisam ser atualizados no local, adicionando um sufixo de nome de arquivo adequado, por exemplo, ". old".  
  
- Backup de cópia significa que um projeto copia todos os itens de projeto para um local de backup fornecido pelo usuário. Os arquivos relevantes no local do projeto original são atualizados.  
  
## <a name="how-upgrade-works"></a>Como funciona a atualização  
 Quando uma solução criada em uma versão anterior do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] é aberta em uma versão mais recente, o IDE verifica o arquivo da solução para determinar se ele precisa ser atualizado. Se a atualização for necessária, o **Assistente de atualização** será iniciado automaticamente para orientar o usuário durante o processo de atualização.  
  
 Quando uma solução precisa ser atualizada, ela consulta cada fábrica de projetos em busca de sua estratégia de atualização. A estratégia determina se a fábrica de projetos dá suporte ao backup de cópia ou de um conjunto. As informações são enviadas para o **Assistente de atualização**, que coleta as informações necessárias para o backup e apresenta as opções aplicáveis ao usuário.  
  
### <a name="multi-project-solutions"></a>Soluções de vários projetos  
 Se uma solução contiver vários projetos e as estratégias de atualização forem diferentes, como quando um projeto C++ oferece suporte apenas a backup de SxS e um projeto Web que oferece suporte apenas a backup de cópia, as fábricas de projeto devem negociar a estratégia de atualização.  
  
 A solução consulta cada fábrica de projetos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Em seguida, ele chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver se arquivos de projeto globais precisam de atualização e para determinar as estratégias de atualização com suporte. O **Assistente de atualização** é invocado.  
  
 Depois que o usuário conclui o assistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> é chamado em cada fábrica de projetos para executar a atualização real. Para facilitar o backup, os métodos IVsProjectUpgradeViaFactory fornecem o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> serviço para registrar em log os detalhes do processo de atualização. Este serviço não pode ser armazenado em cache.  
  
 Depois de atualizar todos os arquivos globais relevantes, cada fábrica de projetos pode optar por criar uma instância de um projeto. A implementação do projeto deve dar suporte a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado para atualizar todos os itens de projeto relevantes.  
  
> [!NOTE]
> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método não fornece o serviço SVsUpgradeLogger. Esse serviço pode ser obtido chamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Práticas Recomendadas  
 Use o <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> serviço para verificar se você pode editar um arquivo antes de editá-lo e pode salvá-lo antes de salvá-lo. Isso ajudará as implementações de backup e atualização a manipular arquivos de projeto sob controle do código-fonte, arquivos com permissões insuficientes e assim por diante.  
  
 Use o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> serviço durante todas as fases de backup e atualização para fornecer informações sobre o êxito ou a falha do processo de atualização.  
  
 Para obter mais informações sobre como fazer backup e atualizar projetos, consulte os comentários para IVsProjectUpgrade em vsshell2. idl.  
  
## <a name="see-also"></a>Consulte Também  
 [Projeto](../../extensibility/internals/projects.md)   
 [Atualizando projetos personalizados](../../misc/upgrading-custom-projects.md)   
 [Atualizando Itens de Projeto](../../misc/upgrading-project-items.md)
