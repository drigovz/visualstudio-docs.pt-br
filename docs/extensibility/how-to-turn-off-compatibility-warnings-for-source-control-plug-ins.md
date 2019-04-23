---
title: Desativar avisos de compatibilidade para Plug-ins de controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1a113dc3b4a4b3a8a4482dd092878851d740c6e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112189"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Como: Desativar avisos de compatibilidade para plug-ins de controle de origem
Um usuário pode ver vários avisos de compatibilidade durante o emprego de controle de origem no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Os avisos apresentados dependem dos recursos de plug-in de controle do código-fonte e podem ser desabilitados como detalhada aqui.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para desabilitar o aviso: "Para garantir a integração de controle de código-fonte ideal com o Visual Studio"

- Defina a seguinte entrada do registro (adicionando o valor, se necessário):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Esse aviso é exibido para todos os não -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para desabilitar o aviso: "O provedor de controle de origem instalado não oferece suporte a todos os recursos"

- Defina os seguintes valores de registro de dois (adicionando os valores se necessário):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Esse aviso é exibido se o plug-in de controle do código-fonte não suporte explicitamente reentrância para vários projetos (ou seja, se ele pode verificar em apenas um arquivo e projeto cada vez).

     É melhor dar suporte a reentrância (`SCC_CAP_REENTRANT` capacidade); portanto, irá remover este aviso. No entanto, se esse suporte não for possível, essas entradas do Registro podem ser definidas.

## <a name="see-also"></a>Consulte também
- [Sinalizadores de recurso](../extensibility/capability-flags.md)