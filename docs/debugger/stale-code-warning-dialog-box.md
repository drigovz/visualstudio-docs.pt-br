---
title: Obsoleto de caixa de diálogo de aviso de código | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82731ba2c22c18b880e8a035712280eb5e5afe68
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877447"
---
# <a name="stale-code-warning-dialog-box"></a>Caixa de diálogo Aviso de Código Obsoleto

Essa caixa de diálogo aparece quando você fez alterações no código nativo que **Editar e Continuar** não pôde aplicar imediatamente. Como resultado, alguns códigos nativos no quadro de pilhas atual agora está expirado, ou seja, obsoleto. Para saber mais, confira [Editar e Continuar (C++)](edit-and-continue-visual-cpp.md).

**Não mostrar esta caixa de diálogo novamente**

Se você marcar essa caixa de seleção, Editar e Continuar aplicará as alterações de código sem solicitar permissão no futuro. Você pode ativar esse aviso sobre novamente indo para a caixa de diálogo **Opções**, abrindo a pasta **Depuração**, clicando na página **Editar e Continuar** e selecionando **Avisar sobre código obsoleto**.

## <a name="see-also"></a>Consulte também

- [Alterações de código com suporte (C++)](supported-code-changes-cpp.md)
- [Caixa de diálogo Editar e Continuar, Depuração, Opções](edit-and-continue.md)