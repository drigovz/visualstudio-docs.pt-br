---
title: Extensibilidade do serviço de linguagem herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194987"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilidade do serviço de linguagem herdado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um serviço de linguagem fornece suporte específico a um idioma para a edição do código-fonte no IDE.  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente de implementar recursos de serviço de linguagem é usar extensões de MEF. Para saber mais sobre a nova maneira de implementar um serviço de linguagem, consulte [extensões de serviço de editor e linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
 Esta seção aborda a estrutura e a implementação de um serviço de linguagem herdado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Migrando um serviço de linguagem herdado](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Explica como atualizar um serviço de linguagem do Visual Studio 2008 para a versão mais recente.  
  
 [Conceitos básicos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-essentials.md)  
 Fornece informações importantes sobre como desenvolver serviços de linguagem para integrar uma linguagem de programação ao Visual Studio.  
  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Fornece links para tópicos que podem ajudá-lo a criar um serviço de idioma.  
  
 [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fornece informações sobre como dar suporte ao realce de sintaxe em um serviço de linguagem.  
  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fornece informações sobre como usar a MPF (estrutura de pacote gerenciada) para implementar um serviço de linguagem repleto de recursos em código gerenciado.  
  
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Descreve bibliotecas e ferramentas que permitem procurar exibições de árvore de símbolos no IDE.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md)  
 Fornece uma visão geral dos editores do Visual Studio.  
  
 [Suporte do serviço de linguagem para depuração](../../extensibility/internals/language-service-support-for-debugging.md)  
 Fornece informações sobre o e um link para o SDK de depuração do Visual Studio, que contém as informações necessárias para criar e personalizar os componentes do depurador usados para depurar programas.
