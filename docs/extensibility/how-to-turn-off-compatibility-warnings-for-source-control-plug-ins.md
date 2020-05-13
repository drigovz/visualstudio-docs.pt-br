---
title: Desativar avisos de compatibilidade para plug-ins de controle de origem | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710719"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Como: Desativar avisos de compatibilidade para plug-ins de controle de origem
Um usuário pode ver vários avisos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]compatibilidade ao empregar o controle de origem em . Os avisos apresentados dependem das capacidades do plug-in de controle de origem e podem ser desativados conforme detalhado aqui.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para desativar o aviso: "Para garantir a integração ideal de controle de origem com o Visual Studio"

- Defina a seguinte entrada de registro (adicionando o valor, se necessário):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Este aviso é exibido para[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] todos os não-plug-ins.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para desativar o aviso: "O provedor de controle de origem instalado não suporta todos os recursos"

- Defina os dois valores de registro a seguir (adicionando os valores, se necessário):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Este aviso é exibido se o plug-in de controle de origem não suportar explicitamente a reentrada para vários projetos (isto é, se ele pode verificar apenas um arquivo e projeto por vez).

     É melhor apoiar a reentrada (capacidade);`SCC_CAP_REENTRANT` fazendo isso removerá este aviso. No entanto, se esse suporte não for possível, essas entradas de registro podem ser definidas.

## <a name="see-also"></a>Confira também
- [Bandeiras de capacidade](../extensibility/capability-flags.md)
