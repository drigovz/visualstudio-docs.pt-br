---
title: Desativar os avisos de compatibilidade para plug-ins de controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710719"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Como desativar avisos de compatibilidade para plug-ins de controle do código-fonte
Um usuário pode ver vários avisos de compatibilidade ao empregar o controle do código-fonte no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Os avisos apresentados dependem dos recursos do plug-in de controle do código-fonte e podem ser desabilitados como detalhados aqui.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para desabilitar o aviso: "para garantir a integração do controle do código-fonte ideal com o Visual Studio"

- Defina a seguinte entrada do registro (adicionando o valor, se necessário):

   **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Esse aviso é exibido para todos os não [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para desabilitar o aviso: "o provedor de controle do código-fonte instalado não dá suporte a todos os recursos"

- Defina os dois valores de registro a seguir (adicionando os valores, se necessário):

     **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Esse aviso será exibido se o plug-in de controle do código-fonte não der suporte explicitamente à reentrância para vários projetos (ou seja, se ele puder fazer check-in de apenas um arquivo e projeto de cada vez).

     É melhor dar suporte à reentrância ( `SCC_CAP_REENTRANT` funcionalidade); fazer isso removerá esse aviso. No entanto, se esse suporte não for possível, essas entradas de registro poderão ser definidas.

## <a name="see-also"></a>Confira também
- [Sinalizadores de capacidade](../extensibility/capability-flags.md)
