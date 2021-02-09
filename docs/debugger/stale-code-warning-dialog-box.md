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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4ea2004680a60fcd2c90a57b19f719c0412ee53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861238"
---
# <a name="stale-code-warning-dialog-box"></a>Caixa de diálogo Aviso de Código Obsoleto

Essa caixa de diálogo aparece quando você fez alterações no código nativo que **Editar e Continuar** não pôde aplicar imediatamente. Como resultado, alguns códigos nativos no quadro de pilhas atual agora está expirado, ou seja, obsoleto. Para saber mais, confira [Editar e Continuar (C++)](edit-and-continue-visual-cpp.md).

**Não mostrar esta caixa de diálogo novamente**

Se você marcar essa caixa de seleção, Editar e Continuar aplicará as alterações de código sem solicitar permissão no futuro. Você pode ativar esse aviso sobre novamente indo para a caixa de diálogo **Opções**, abrindo a pasta **Depuração**, clicando na página **Editar e Continuar** e selecionando **Avisar sobre código obsoleto**.

## <a name="see-also"></a>Consulte também

- [Alterações de código suportadas (C++)](supported-code-changes-cpp.md)
- [Caixa de diálogo Editar e Continuar, Depuração, Opções](edit-and-continue.md)