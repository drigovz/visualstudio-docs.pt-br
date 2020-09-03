---
title: Onde posso pesquisar códigos de erro Win32? | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8e3dda1b728cd631efe8a84913af3d5c475138d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72728028"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Onde posso pesquisar códigos de erro Win32?
WINERROR.H no diretório INCLUDE da instalação do sistema padrão contém as definições do código de erro para as funções de API do Win32.

 Você pode pesquisar um código de erro digitando o código na janela **Inspeção** ou na caixa de diálogo **QuickWatch**. Por exemplo:

`0x80000004,hr`

## <a name="see-also"></a>Confira também
- [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)