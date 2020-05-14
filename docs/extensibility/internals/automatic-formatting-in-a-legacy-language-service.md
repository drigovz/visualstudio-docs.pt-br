---
title: Formatação automática em um serviço de idioma legado | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709987"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatação automática em um serviço de idioma legado
Com a formatação automática, um serviço de idioma insere automaticamente um trecho de código quando um usuário começa a digitar uma construção de código conhecida.

## <a name="automatic-formatting-behavior"></a>Comportamento de formatação automática
 Por exemplo, quando você digita *se*, o serviço de idioma insere automaticamente chaves correspondentes ou se você pressionar a tecla ENTER, o serviço de idioma força o ponto de inserção na nova linha para o nível de recuo apropriado, dependendo se a linha anterior abre um novo escopo.

 O filtro de comando usado para o resto do serviço de idiomas também pode ser usado para formatação automática. Você também pode destacar aparelhos correspondentes chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.

## <a name="see-also"></a>Confira também
- [Desenvolva um serviço de linguagem legado](../../extensibility/internals/developing-a-legacy-language-service.md)
