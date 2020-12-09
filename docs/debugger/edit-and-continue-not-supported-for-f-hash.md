---
title: 'Editar e continuar não tem suporte para F # | Microsoft Docs'
description: 'Não há suporte para editar e continuar na depuração F #. As edições no código durante a depuração não são aplicadas à origem, portanto, o código que está sendo depurado não corresponde à origem.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33d1e8379e71c41e42cbf761ccdfe740342ee642
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863082"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Editar e Continuar não suportado para F# #
A função Editar e Continuar não tem suporte quando você depura o código F#. As edições ao código F# são possíveis durante uma sessão de depuração mas devem ser evitadas. As alterações de código não são aplicadas durante a sessão de depuração. Como consequência, todas as edições feitas no código F# enquanto você depura resultarão no código-fonte que não corresponde ao código que está sendo depurado.
