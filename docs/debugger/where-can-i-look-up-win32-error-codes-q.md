---
title: Onde posso pesquisar códigos de erro Win32? | Microsoft Docs
description: Para pesquisar um código de erro Win32, insira-o em Watch ou QuickWatch. Por exemplo, "0x80000004, HR". As definições de código de erro estão em INCLUDE\WINERROR.H.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 44a006be3b6ecad3ef723c00154354cb35df0049
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149281"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Onde posso pesquisar códigos de erro Win32?
WINERROR.H no diretório INCLUDE da instalação do sistema padrão contém as definições do código de erro para as funções de API do Win32.

 Você pode pesquisar um código de erro digitando o código na janela **Inspeção** ou na caixa de diálogo **QuickWatch**. Por exemplo:

`0x80000004,hr`

## <a name="see-also"></a>Confira também
- [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)