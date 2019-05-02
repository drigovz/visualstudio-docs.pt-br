---
title: Editar e continuar não tem suporte para F# | Microsoft Docs
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
ms.openlocfilehash: ceb0ca767b1ac6364e103925fb86ed639c3d321d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851168"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Editar e Continuar não suportado para F# #
A função Editar e Continuar não tem suporte quando você depura o código F#. As edições ao código F# são possíveis durante uma sessão de depuração mas devem ser evitadas. As alterações de código não são aplicadas durante a sessão de depuração. Como consequência, todas as edições feitas no código F# enquanto você depura resultarão no código-fonte que não corresponde ao código que está sendo depurado.
