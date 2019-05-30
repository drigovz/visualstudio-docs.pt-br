---
title: O que há de novo no controle de origem no SDK do Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e12776c21d345d60992eeff4963498bcd7d56678
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323258"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>O que há de novo no controle de origem para o SDK do Visual Studio 2015

No [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], você pode fornecer uma solução de controle do código-fonte profundamente integrado com a implementação de um VSPackage de controle do código-fonte. Esta seção descreve os recursos de controle do código-fonte VSPackages e fornece uma visão geral das etapas de implementação.

## <a name="the-source-control-vspackage"></a>O VSPackage de controle do código-fonte

Visual Studio dá suporte a dois tipos de soluções de controle do código-fonte. Todas as versões do Visual Studio, você ainda pode integrar uma API de plug-in de controle de origem com base no plug-in. Você também pode criar um VSPackage de controle do código-fonte que fornece uma integração profunda, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] caminho adequado para soluções de controle do código-fonte que exigem um alto nível de sofisticação e autonomia.

Um VSPackage pode adicionar praticamente qualquer tipo de funcionalidade para o Visual Studio. Um VSPackage de controle do código-fonte fornece um recurso de controle do código-fonte completo para o Visual Studio, da interface do usuário apresentada ao usuário para a comunicação de back-end com o sistema de controle do código-fonte.

Implementar um VSPackage de controle do código-fonte exige uma estratégia "tudo ou nada". O criador de um VSPackage de controle do código-fonte deve investir uma quantidade significativa de esforço na implementação de um número de interfaces de controle do código-fonte e os novos elementos de interface do usuário (caixas de diálogo, menus e barras de ferramentas) para cobrir a funcionalidade de controle de origem inteiro, bem como interfaces necessário de qualquer pacote para integrar-se com êxito com o Visual Studio.

As etapas a seguir dão uma visão geral do que é necessário para implementar um pacote de controle do código-fonte. Para obter detalhes, consulte [criando um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Crie um VSPackage que oferece um serviço de controle de origem particular.

2. Implementar as interfaces nos serviços relacionados ao controle do código-fonte que são dedicaram pelo Visual Studio (por exemplo, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface).

3. Registre o VSPackage de controle de origem.

4. Implemente o controle de fonte de todos os da interface do usuário, incluindo itens de menu, caixas de diálogo, barras de ferramentas e menus de contexto.

5. Todos os eventos relacionados ao controle do código-fonte são passados para o controle de origem VSackage quando ele estiver ativo e deve ser tratado pelo VSPackage.

6. O VSPackage de controle de origem deve escutar eventos, como aqueles Implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interface, bem como eventos de documento de projeto da faixa (TPD) (conforme implementado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface) e tomar as medidas necessárias.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Visão geral](../../extensibility/internals/source-control-integration-overview.md)
- [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)