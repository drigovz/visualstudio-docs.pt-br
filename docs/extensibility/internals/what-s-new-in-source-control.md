---
title: Novidades no Controle de Fontes no Visual Studio 2015 SDK | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703405"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>O que há de novo no Controle de Fontes para o Visual Studio 2015 SDK

No [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], você pode fornecer uma solução de controle de origem profundamente integrada implementando um VSPackage de controle de origem. Esta seção descreve os recursos do controle de origem VSPackages e fornece uma visão geral das etapas de implementação.

## <a name="the-source-control-vspackage"></a>O pacote VS de controle de origem

O Visual Studio suporta dois tipos de soluções de controle de origem. Em todas as versões do Visual Studio, você ainda pode integrar um plug-in baseado em API de controle de fonte. Você também pode criar um VSPackage para controle [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] de origem que fornece uma integração profunda, caminho adequado para soluções de controle de origem que requerem um alto nível de sofisticação e autonomia.

Um VSPackage pode adicionar quase qualquer tipo de funcionalidade ao Visual Studio. Um controle de origem VSPackage fornece um recurso completo de controle de origem para o Visual Studio, desde a UI apresentada ao usuário até a comunicação back-end com o sistema de controle de origem.

Implementar um controle de origem VSPackage requer uma estratégia de "tudo ou nada". O criador de um controle de origem VSPackage deve investir uma quantidade significativa de esforço na implementação de uma série de interfaces de controle de fonte e novos elementos de interface (caixas de diálogo, menus e barras de ferramentas) para cobrir toda a funcionalidade de controle de origem, bem como interfaces necessárias de qualquer pacote para se integrar com sucesso com o Visual Studio.

As etapas a seguir fornecem uma visão geral do que é necessário para implementar um pacote de controle de origem. Para obter detalhes, consulte [Criando um VsPackage de Controle de Origem](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Crie um VSPackage que ofereça um serviço de controle de origem privada.

2. Implemente as interfaces nos serviços relacionados ao controle de origem que <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> são <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> oferecidos pelo Visual Studio (por exemplo, a interface).

3. Registre seu controle de origem VSPackage.

4. Implemente todas as interfaces de controle de origem, incluindo itens de menu, caixas de diálogo, barras de ferramentas e menus de contexto.

5. Todos os eventos relacionados ao controle de origem são passados para o seu vSackage de controle de origem quando ele está ativo e deve ser tratado pelo seu VSPackage.

6. Seu controle de origem VSPackage deve ouvir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> eventos como aqueles que implementam a interface, bem <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> como eventos TPD (Track Project Document) (como implementado pela interface) e tomar as medidas necessárias.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Visão geral](../../extensibility/internals/source-control-integration-overview.md)
- [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)
