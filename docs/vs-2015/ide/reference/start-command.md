---
title: Comando Iniciar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c334f52ba080329ef5cbd6dfde1e3e3beed1dc70
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658156"
---
# <a name="start-command"></a>Comando Iniciar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inicia a depuração do projeto de inicialização.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 Opcional. O endereço no qual o programa suspende a execução, semelhante a um ponto de interrupção no código-fonte. Este argumento é válido apenas no modo de depuração.  
  
## <a name="remarks"></a>Comentários  
 O comando **Iniciar**, quando executado, executa uma operação RunToCursor para o endereço especificado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo inicia o depurador e ignora todas as exceções que ocorrerem.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
