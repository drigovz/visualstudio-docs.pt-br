---
title: Formatação automática em um serviço de linguagem herdada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709987"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatação automática em um serviço de idioma herdado
Com a formatação automática, um serviço de idioma insere automaticamente um trecho de código quando um usuário começa a digitar uma construção de código conhecida.

## <a name="automatic-formatting-behavior"></a>Comportamento de formatação automática
 Por exemplo, quando você digita *se*, o serviço de idioma insere automaticamente as chaves correspondentes ou, se você pressionar a tecla Enter, o serviço de idioma forçará o ponto de inserção na nova linha para o nível de recuo apropriado, dependendo se a linha anterior abre um novo escopo.

 O filtro de comando usado para o restante do serviço de idioma também pode ser usado para formatação automática. Você também pode realçar as chaves correspondentes chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Confira também
- [Desenvolver um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
