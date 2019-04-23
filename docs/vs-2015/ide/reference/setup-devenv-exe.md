---
title: -Setup (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6e5bbbf3a1a9601a46aa9d3080f0d20583b43d22
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670232"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Força o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a mesclar os metadados de recursos que descrevem menus, barras de ferramentas e grupos de comando de todos os VSPackages disponíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Comentários  
 Esta opção não aceita nenhum argumento. O comando `devenv /setup` geralmente é fornecido como a última etapa do processo de instalação. Usar a opção `/setup` não inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 É necessário executar `devenv` como administrador para usar as opções [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra a última etapa na instalação de uma versão do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que inclui os VSPackages.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
