---
title: Implementando uma função de linguagem herdado1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3218a8cf1c61fb9b88520702a953f2288e19b3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855881"
---
# <a name="implementing-a-legacy-language-service"></a>Implementando um serviço de linguagem herdado
Você pode usar classes do framework de pacote gerenciado (MPF) para implementar um serviço de linguagem herdada que dá suporte a uma ampla variedade de recursos, como realce de sintaxe, correspondência de chaves e preenchimento do IntelliSense.  
  
 Serviços de linguagem herdado são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de linguagem, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API mais rápido possível. Isso melhorará o desempenho do seu serviço de linguagem e permitem que você tirar proveito dos novos recursos do editor.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-overview.md)  
 Uma visão geral dos recursos de serviço de linguagem que têm suporte no MPF.  
  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Descreve o que é necessário para implementar um serviço de linguagem usando MPF.  
  
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Descreve as etapas necessárias para registrar um serviço de linguagem baseada em MPF com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Analisador e scanner do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Descreve os dois analisadores que são necessários para implementar todos os recursos de um serviço de linguagem usando o MPF.  
  
 [Passo a passo: Criar um serviço de linguagem herdado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Fornece as etapas básicas que são necessários para implementar um serviço de linguagem MPF em um VSPackage.  
  
 [Passo a passo: Obtendo uma lista de trechos de código instalados (implementação herdada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Demonstra as técnicas de recuperar uma lista de trechos de código instalado.  
  
 [Recursos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md)  
 Fornece links para tópicos que detalham o que deve ser feito para implementar todos os recursos de um serviço de linguagem usando MPF.