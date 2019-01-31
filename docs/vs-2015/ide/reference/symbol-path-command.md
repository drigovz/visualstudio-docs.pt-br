---
title: Comando de caminho de símbolo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da136a76a06182bd32ebf2ca868e77f202087e45
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767270"
---
# <a name="symbol-path-command"></a>Comando demarcador do Símbolo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Define a lista de diretórios para o depurador pesquisar símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Arguments  
 `pathname`  
 Opcional. Uma lista de caminhos delimitada por ponto-e-vírgula para que o depurador pesquise símbolos.  
  
## <a name="remarks"></a>Comentários  
 Se nenhum `pathname` for especificado, o comando listará os caminhos de símbolo atual.  
  
## <a name="example"></a>Exemplo  
 Este exemplo adiciona dois caminhos à lista de diretórios de símbolo.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe uma lista delimitada por ponto-e-vírgula dos caminhos de símbolo atuais.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Consulte também  
 [Janela Comando](../../ide/reference/command-window.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
