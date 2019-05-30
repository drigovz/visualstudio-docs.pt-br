---
title: Extensões de serviço do Editor e linguagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1df6f65db70425650fc2860bf5ddf6e2d2e203c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353378"
---
# <a name="editor-and-language-service-extensions"></a>Extensões de serviços do Editor e linguagem
Você pode estender a maioria dos recursos do editor de código do Visual Studio. O editor é baseado no Windows Presentation Foundation (WPF) e é escrito em código gerenciado. Embora esse design difere os designs em versões anteriores do Visual Studio, ele fornece a maioria dos mesmos recursos. Para estender o editor, use o MEF Managed Extensibility Framework ().

 O SDK do Visual Studio fornece adaptadores conhecidos como *shims* para dar suporte a VSPackages que foram escritos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos que você atualize para a nova tecnologia para obter melhor desempenho e confiabilidade.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Criar uma extensão com um modelo de item editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introdução ao uso de modelos de item do Editor.|
|[Estender os serviços do editor e linguagem](../extensibility/extending-the-editor-and-language-services.md)|Links para documentos que apresentam o design e os recursos do editor de núcleo e mostram como estendê-lo.|
|[Interfaces herdadas no editor](../extensibility/legacy-interfaces-in-the-editor.md)|Links para documentos que explicam como acessar o editor principal do código existente.|
|[Criar designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Links para documentos que explicam como criar editores personalizados.|
|[Extensibilidade do serviço de linguagem herdado](../extensibility/internals/legacy-language-service-extensibility.md)|Contém links para documentos que descrevem como integrar a linguagens de programação no Visual Studio.|
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Apresenta o Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Apresenta o Windows Presentation Foundation (WPF).|