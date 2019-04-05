---
title: Formatação automática em um serviço de linguagem herdado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929558"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatação automática em um serviço de linguagem herdado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Com a formatação automática, um serviço de linguagem insere um trecho de código automaticamente quando um usuário começa a digitar uma construção de código conhecidas.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento da formatação automática  
 Por exemplo, quando você digita `if`, o serviço de linguagem insere automaticamente chaves correspondentes, ou se você pressionar a tecla ENTER, o serviço de linguagem força o ponto de inserção na nova linha para o nível de recuo apropriado, dependendo se anterior linha abre um novo escopo.  
  
 O filtro de comando usado para o resto do serviço de linguagem também pode ser usado para formatação automática. Você também pode realçar chaves correspondentes chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
