---
title: Extensões de Serviços de Editor e Linguagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712027"
---
# <a name="editor-and-language-service-extensions"></a>Extensões de serviços de editor e linguagem
Você pode estender a maioria dos recursos do editor de código sateliteria isat O editor é baseado no Windows Presentation Foundation (WPF) e está escrito em código gerenciado. Embora este design difere dos designs em versões anteriores do Visual Studio, ele fornece a maioria das mesmas características. Para estender o editor, use o Mef (Managed Extensibility Framework, quadro de extensibilidade gerenciada).

 O Visual Studio SDK fornece adaptadores conhecidos como *shims* para suportar VSPackages que foram escritos para versões anteriores. No entanto, se você tem um VSPackage existente, recomendamos que você atualize-o para a nova tecnologia para obter melhor desempenho e confiabilidade.

## <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Crie uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introdução ao uso dos modelos de itens do Editor.|
|[Estender o editor e os serviços de idiomas](../extensibility/extending-the-editor-and-language-services.md)|Links para documentos que introduzem o design e os recursos do editor principal e mostram como estendê-lo.|
|[Interfaces legadas no editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Links para documentos que explicam como acessar o editor principal a partir do código existente.|
|[Crie editores e designers personalizados](../extensibility/creating-custom-editors-and-designers.md)|Links para documentos que explicam como criar editores personalizados.|
|[Extensibilidade do serviço de linguagem legado](../extensibility/internals/legacy-language-service-extensibility.md)|Links para documentos que descrevem como integrar linguagens de programação no Visual Studio.|
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Introduz o Quadro de Extensibilidade Gerenciada (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Introduz a Fundação de Apresentação do Windows (WPF).|
