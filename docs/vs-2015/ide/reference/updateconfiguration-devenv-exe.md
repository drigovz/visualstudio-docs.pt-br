---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ffc9410d64f58fff771a0e9b251ee1131eaea5e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670024"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Notifica o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para mesclar os pacotes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no sistema e verificar o cache MEF para as alterações.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] executa este comando automaticamente quando você instala um pacote VSIX. Você deve executar `devenv.exe /updateconfiguration` após a aplicação de patch em seus arquivos de modo que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] atualize o cache MEF. Isso permite que você avalie se a correção é adequada.  
  
## <a name="example"></a>Exemplo  
 A linha de comando a seguir faz com que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mescle os pacotes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no sistema e verifique o cache MEF para quaisquer eventuais alterações.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
