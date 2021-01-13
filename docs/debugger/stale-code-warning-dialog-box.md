---
title: Caixa de diálogo de aviso de código obsoleto | Microsoft Docs
description: Leia sobre a caixa de diálogo aviso de código obsoleto, que aparece quando você fez alterações no código nativo que o editar e continuar não podiam aplicar imediatamente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb2666b3b57c8f84c81e181355f096674543445
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150321"
---
# <a name="stale-code-warning-dialog-box"></a>Caixa de diálogo Aviso de Código Obsoleto

Essa caixa de diálogo aparece quando você fez alterações no código nativo que **Editar e Continuar** não pôde aplicar imediatamente. Como resultado, alguns códigos nativos no quadro de pilhas atual agora está expirado, ou seja, obsoleto. Para saber mais, confira [Editar e Continuar (C++)](edit-and-continue-visual-cpp.md).

**Não mostrar esta caixa de diálogo novamente**

Se você marcar essa caixa de seleção, Editar e Continuar aplicará as alterações de código sem solicitar permissão no futuro. Você pode ativar esse aviso sobre novamente indo para a caixa de diálogo **Opções**, abrindo a pasta **Depuração**, clicando na página **Editar e Continuar** e selecionando **Avisar sobre código obsoleto**.

## <a name="see-also"></a>Confira também

- [Alterações de código suportadas (C++)](supported-code-changes-cpp.md)
- [Caixa de diálogo Editar e Continuar, Depuração, Opções](edit-and-continue.md)