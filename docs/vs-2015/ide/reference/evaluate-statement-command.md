---
title: Comando Avaliar Instrução | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f774458eb63d9e56b99a635e7b32309375a903ef
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669231"
---
# <a name="evaluate-statement-command"></a>Comando Avaliar Instrução
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avalia e exibe a instrução fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Necessário. A instrução a ser avaliada.  
  
## <a name="remarks"></a>Comentários  
 A janela usada para inserir o comando **EvaluateStatement** determina se um sinal de igual (=) é interpretado como um operador de comparação ou um operador de atribuição.  
  
 Na janela **Comando**, um sinal de igual (=) é interpretado como um operador de comparação. Dessa forma, por exemplo, se os valores das variáveis `a` e `b` forem diferentes, o comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 retornará um valor de `false`.  
  
 Na janela **Imediato**, por outro lado, um sinal de igual (=) é interpretado como um operador de atribuição. Assim, por exemplo, o comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 atribuirá à variável `a` o valor da variável `b`.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comando Imprimir](../../ide/reference/print-command.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
