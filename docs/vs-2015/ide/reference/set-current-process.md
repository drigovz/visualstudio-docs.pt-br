---
title: Set Current Process | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be451ee1a0b4361e44c8be96713872ca0ee3bd76
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768842"
---
# <a name="set-current-process"></a>Definir processo atual
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Define o processo especificado como o processo ativo no depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Necessário. O índice do processo.  
  
## <a name="remarks"></a>Comentários  
 Você pode se conectar a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento. Você pode usar o comando `SetCurrentProcess` para definir o processo ativo.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
