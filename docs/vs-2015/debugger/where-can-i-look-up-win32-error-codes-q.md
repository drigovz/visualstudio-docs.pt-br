---
title: Onde posso pesquisar códigos de erro Win32? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d403315a2320589f69174109d55c8726ffd5f673
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925825"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Onde posso pesquisar códigos de erro Win32?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WINERROR.H no diretório INCLUDE da instalação do sistema padrão contém as definições do código de erro para as funções de API do Win32.  
  
 Você pode pesquisar um código de erro digitando o código na janela **Inspeção** ou na caixa de diálogo **QuickWatch**. Por exemplo:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)
