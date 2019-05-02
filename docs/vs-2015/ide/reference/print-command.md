---
title: Comando Print | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666540"
---
# <a name="print-command"></a>Comando Imprimir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avalia uma expressão ou exibe o texto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Necessário. A expressão a ser avaliada ou o texto a ser exibido.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o ponto de interrogação (?) como um alias para esse comando. Assim, por exemplo, o comando  
  
```  
>Debug.Print expA  
```  
  
 também podem ser gravado  
  
```  
>? expA  
```  
  
 As duas versões desse comando retornarão o valor atual da expressão `expA`.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comando Evaluate Statement](../../ide/reference/evaluate-statement-command.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
