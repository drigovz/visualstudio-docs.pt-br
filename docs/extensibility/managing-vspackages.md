---
title: Gerenciando VSPackages | Microsoft Docs
description: Saiba mais sobre como gerenciar o VSPackages, para que você saiba quando pode simplesmente usar o gerenciamento de VSPackage padrão fornecido pelo Visual Studio e como e quando personalizá-lo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b0e3b95ee3c715eb21028b6c156b7a62ea82d41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943212"
---
# <a name="manage-vspackages"></a>Gerenciar VSPackages
Na maioria dos casos, você não precisa se preocupar com o gerenciamento de VSPackages, já que os modelos de projeto e item registram e carregam o pacote automaticamente. No entanto, em algumas circunstâncias, talvez seja necessário aprender um pouco mais para gerenciar seu pacote.

## <a name="use-the-experimental-instance"></a>Usar a instância experimental
 Para saber mais sobre a instância experimental, consulte [a instância experimental](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrar e cancelar o registro de VSPackages
 Para saber como registrar e cancelar o registro de VSPackages e outros tipos de extensão, consulte [registrar e cancelar o registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Carregar um VSPackage
 VSPackages pode ser definido como AutoLoad quando um GUID de CMDUICONTEXT específico é ativado. Para obter mais informações, consulte [Load VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Usar AsyncPackage para carregar VSPackages em segundo plano
 A `AsyncPackage` classe habilita o carregamento de pacotes em um thread em segundo plano para melhorar a capacidade de resposta da interface do usuário no Visual Studio. Para obter mais informações, consulte [como: usar AsyncPackage para carregar VSPackages em segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interface do usuário baseado em regra para extensões
 Os contextos de interface do usuário baseados em regras permitem que os autores de extensão definam as condições exatas sob as quais um contexto de interface do usuário é ativado e VSPackages associado são carregados. Para obter mais informações, consulte [como usar o contexto de interface do usuário com base em regras para extensões do Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnosticar o desempenho da extensão
As extensões podem afetar o desempenho de inicialização e de carga da solução. Saiba como o impacto da extensão do Visual Studio é calculado e como ele pode ser analisado localmente para testar se uma extensão pode ser mostrada como uma extensão de impacto no desempenho. Para obter mais informações, consulte [como: diagnosticar o desempenho da extensão](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Solucionar problemas de VSPackages
 Descubra as técnicas para solucionar problemas de VSPackages que não carregam ou estão ocorrendo erros: [solucionar problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Confira também
- [VSPackages](../extensibility/internals/vspackages.md)
