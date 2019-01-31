---
title: Comando Ativar/desativar ponto de interrupção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 11f0598fa20a5293d662bdbb23b7f67c6c0c80b2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793168"
---
# <a name="toggle-breakpoint-command"></a>Comando Ativar/Desativar Ponto de Interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Ativa ou desativa o ponto de interrupção dependendo de seu estado atual, no local atual do arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Opcional. Se o texto for especificado, a linha será marcada como um ponto de interrupção nomeado. Caso contrário, a linha será marcada como um ponto de interrupção sem nome, semelhante ao que acontece quando você pressiona F9.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ativa/desativa o ponto de interrupção atual.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
