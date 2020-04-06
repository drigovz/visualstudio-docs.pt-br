---
title: Gerenciamento de pacotes VS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702648"
---
# <a name="manage-vspackages"></a>Gerenciar VSPackages
Na maioria dos casos, você não precisa se preocupar com o gerenciamento de VSPackages, uma vez que os modelos de projeto e itens registram e carregam o pacote automaticamente. No entanto, em algumas circunstâncias, você pode precisar aprender um pouco mais para gerenciar seu pacote.

## <a name="use-the-experimental-instance"></a>Use a instância experimental
 Para saber mais sobre a instância experimental, consulte [A instância experimental](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registre e desregistre VSPacotes
 Para saber como registrar e cancelar o registro VSPackages e outros tipos de extensão, consulte [Registrar e cancelar o registro VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Carregar um VSPackage
 VsPackages podem ser configurados para carregar automaticamente quando um GUID CMDUICONTEXT em particular é ligado. Para obter mais informações, consulte [Load VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Use AsyncPackage para carregar VSPacotes em segundo plano
 A `AsyncPackage` classe permite o carregamento de pacotes em um segmento de fundo para uma melhor capacidade de resposta de IA no Visual Studio. Para obter mais informações, consulte [Como: Usar O SyncPackage para carregar VSPackages em segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interface do ui baseado em regras para extensões
 O Rules-based UI Contexts permite que os autores de extensão definam as condições precisas sob as quais um contexto de interface do ui é ativado e VSPackages associados carregados. Para obter mais informações, consulte [Como: Usar o contexto de interface do ui baseado em regras para extensões do Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnosticar o desempenho da extensão
As extensões podem afetar o desempenho de inicialização e carga de soluções. Saiba como o impacto da extensão do Visual Studio é calculado e como ele pode ser analisado localmente para testar se uma extensão pode ser mostrada como uma extensão que afeta o desempenho. Para obter mais informações, consulte [Como: Diagnosticar o desempenho de extensão](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Solução de problemas VSPacotes
 Descubra as técnicas para solucionar problemas VSPacotes que não carregam ou estão enfrentando erros: [Solução de problemas VSPacotes](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Confira também
- [VSPackages](../extensibility/internals/vspackages.md)
