---
title: Formatação automática em um serviço de linguagem herdada | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157274"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatação automática em um serviço de linguagem herdado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Com a formatação automática, um serviço de idioma insere automaticamente um trecho de código quando um usuário começa a digitar uma construção de código conhecida.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento de formatação automática  
 Por exemplo, quando você digita `if` , o serviço de idioma insere automaticamente chaves correspondentes ou, se você pressiona a tecla Enter, o serviço de idioma força o ponto de inserção na nova linha para o nível de recuo apropriado, dependendo se a linha anterior abre um novo escopo.  
  
 O filtro de comando usado para o restante do serviço de idioma também pode ser usado para formatação automática. Você também pode realçar as chaves correspondentes chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .  
  
## <a name="see-also"></a>Consulte Também  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
