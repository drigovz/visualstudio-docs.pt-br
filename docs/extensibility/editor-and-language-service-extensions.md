---
title: Extensões do editor e do serviço de linguagem | Microsoft Docs
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
ms.openlocfilehash: 78d85cd3651f8769104a61586bea1468e1c21cd2
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414068"
---
# <a name="editor-and-language-service-extensions"></a>Extensões do editor e do serviço de linguagem
Você pode estender a maioria dos recursos do editor de código do Visual Studio. O editor é baseado no Windows Presentation Foundation (WPF) e é escrito em código gerenciado. Embora esse design seja diferente dos projetos em versões anteriores do Visual Studio, ele fornece a maioria dos mesmos recursos. Para estender o editor, use o Managed Extensibility Framework (MEF).

 O SDK do Visual Studio fornece adaptadores conhecidos como *shims* para dar suporte a VSPackages que foram escritos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos atualizá-lo para a nova tecnologia para obter melhor desempenho e confiabilidade.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introdução ao uso dos modelos de item do editor.|
|[Estenda os serviços de editor e linguagem](../extensibility/extending-the-editor-and-language-services.md)|Links para documentos que introduzem o design e os recursos do editor principal e mostram como estendê-lo.|
|[Interfaces herdadas no editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)|Links para documentos que explicam como acessar o editor principal do código existente.|
|[Criar editores e designers personalizados](../extensibility/creating-custom-editors-and-designers.md)|Links para documentos que explicam como criar editores personalizados.|
|[Extensibilidade do serviço de linguagem herdada](../extensibility/internals/legacy-language-service-extensibility.md)|Links para documentos que descrevem como integrar linguagens de programação ao Visual Studio.|
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Apresenta o Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Apresenta o Windows Presentation Foundation (WPF).|