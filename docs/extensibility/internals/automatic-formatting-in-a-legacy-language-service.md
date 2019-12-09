---
title: Formatação automática em um serviço de linguagem herdado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b69419e917a5ab5293af15b21822ca6473a9e292
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344929"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatação automática em um serviço de linguagem herdado
Com a formatação automática, um serviço de linguagem insere um trecho de código automaticamente quando um usuário começa a digitar uma construção de código conhecidas.

## <a name="automatic-formatting-behavior"></a>Comportamento da formatação automática
 Por exemplo, quando você digita *se*, o serviço de linguagem insere automaticamente chaves correspondentes, ou se você pressionar a tecla ENTER, o serviço de linguagem força o ponto de inserção na nova linha para o nível de recuo apropriado, dependendo do Se a linha anterior abre um novo escopo.

 O filtro de comando usado para o resto do serviço de linguagem também pode ser usado para formatação automática. Você também pode realçar chaves correspondentes chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.

## <a name="see-also"></a>Consulte também
- [Desenvolver um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)