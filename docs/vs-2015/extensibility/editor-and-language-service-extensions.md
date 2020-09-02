---
title: Extensões do editor e do serviço de linguagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fa3e4be6ee44011eb1286e3ebf22ee69f8e3397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683109"
---
# <a name="editor-and-language-service-extensions"></a>Editor e extensões do serviço de linguagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode estender a maioria dos recursos do editor de código do Visual Studio. O editor é baseado no Windows Presentation Foundation (WPF) e é escrito em código gerenciado. Embora esse design seja diferente dos projetos em versões anteriores do Visual Studio, ele fornece a maioria dos mesmos recursos. Para estender o editor, use o Managed Extensibility Framework (MEF).  
  
 O SDK do Visual Studio fornece adaptadores conhecidos como *shims* para dar suporte a VSPackages que foram escritos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos atualizá-lo para a nova tecnologia para obter melhor desempenho e confiabilidade.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introdução ao uso dos modelos de item do editor.|  
|[Estender o editor e os serviços de linguagem](../extensibility/extending-the-editor-and-language-services.md)|Links para documentos que introduzem o design e os recursos do editor principal e mostram como estendê-lo.|  
|[Interfaces herdadas no Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Links para documentos que explicam como acessar o editor principal do código existente.|  
|[Criar designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Links para documentos que explicam como criar editores personalizados.|  
|[Extensibilidade do serviço de linguagem herdado](../extensibility/internals/legacy-language-service-extensibility.md)|Links para documentos que descrevem como integrar linguagens de programação ao Visual Studio.|  
|[MEF (Managed Extensibility Framework)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Apresenta o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Apresenta o Windows Presentation Foundation (WPF).|
