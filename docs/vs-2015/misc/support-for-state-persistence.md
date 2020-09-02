---
title: Suporte para persistência de estado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434313"
---
# <a name="support-for-state-persistence"></a>Suporte para persistência de estado
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pode manter o estado de objetos comuns. Por exemplo, as propriedades da solução e do projeto são salvas e restauradas de arquivos de solução e projeto. As configurações de usuário podem ser exportadas e importadas de arquivos de configurações.  
  
 VSPackages normalmente dependem do armazenamento local, no registro do sistema ou na pasta de dados do aplicativo para o usuário ou computador atual. Os valores que exigem uma pequena quantidade de espaço para armazenamento, como inteiros e cadeias de caracteres, normalmente são armazenados no registro do sistema. Os valores que exigem muito espaço para armazenamento, como bitmaps, são salvos em um arquivo. O caminho do arquivo pode ser salvo no registro do sistema. O mecanismo de persistência deve ter permissão para acessar o armazenamento local.  
  
## <a name="support-for-locating-local-storage"></a>Suporte para localização de armazenamento local  
 A <xref:Microsoft.VisualStudio.Shell.Package> classe fornece suporte para localizar informações de estado no registro do sistema ou na pasta de dados do aplicativo para o usuário ou computador atual.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Retorna o caminho da raiz do registro do computador local para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , por exemplo, HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp.  
  
 A raiz do Registro local é obtida do <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> serviço. Se isso não estiver disponível, ele será obtido do <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> atributo do VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Retorna o caminho da raiz do registro do usuário atual (por computador) para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , por exemplo, HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp.  
  
 A raiz do Registro local é obtida do <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> serviço. Se isso não estiver disponível, ele será obtido do atributo DefaultLocalRegistryRoot do VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Retorna o caminho do diretório que serve como um repositório comum de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dados para o usuário móvel atual, por exemplo, C:\Documents and Settings \\ *YourAccountName*\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Retorna o caminho do diretório que serve como um repositório comum de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dados para o usuário não móvel atual, por exemplo, C:\Documents and Settings \\ *YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Consulte Também  
 [Estado de VSPackage](../misc/vspackage-state.md)