---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94e8e87f4440644f76906a70ea09a46282b109c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163372"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inicia o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no modo de segurança, carregando apenas o ambiente e os serviços padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Comentários  
 Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] é iniciado, garantindo assim uma execução estável.  
  
## <a name="description"></a>DESCRIÇÃO  
 O exemplo a seguir inicia o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no modo de segurança.  
  
## <a name="code"></a>Código  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Veja também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
