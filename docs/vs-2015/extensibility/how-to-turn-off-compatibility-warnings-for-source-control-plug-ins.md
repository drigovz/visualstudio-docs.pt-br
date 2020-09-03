---
title: Como desativar os avisos de compatibilidade para plug-ins de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4397b2710a7de4addd97bfcbdb4f8e80e2b9c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204059"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Como desativar avisos de compatibilidade para plug-ins de controle do código-fonte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um usuário pode ver vários avisos de compatibilidade ao empregar o controle do código-fonte no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Os avisos apresentados dependem dos recursos do plug-in de controle do código-fonte e podem ser desabilitados como detalhados aqui.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para desabilitar o aviso: "para garantir a integração do controle do código-fonte ideal com o Visual Studio..."  
  
- Defina a seguinte entrada do registro (adicionando o valor, se necessário):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Esse aviso é exibido para todos os não [!INCLUDE[vsvss](../includes/vsvss-md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para desabilitar o aviso: "o provedor de controle do código-fonte instalado não dá suporte a todos os recursos..."  
  
- Defina os dois valores de registro a seguir (adicionando os valores, se necessário):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Esse aviso será exibido se o plug-in de controle do código-fonte não der suporte explicitamente à reentrância para vários projetos (ou seja, se ele puder fazer check-in de apenas um arquivo e projeto de cada vez).  
  
     É melhor dar suporte à reentrância ( `SCC_CAP_REENTRANT` funcionalidade); fazer isso removerá esse aviso. No entanto, se esse suporte não for possível, essas entradas de registro poderão ser definidas.  
  
## <a name="see-also"></a>Consulte Também  
 [Sinalizadores de capacidade](../extensibility/capability-flags.md)
