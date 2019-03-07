---
title: Comando Listar Origem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae2ed3e8a9c07d59f5b1c2fe2350956a54dfaa66
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54761501"
---
# <a name="list-source-command"></a>Comando Listar Origem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Exibe as linhas de código-fonte especificadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Opções  
 /Count:`number`  
 Opcional. Especifica o número de linhas que serão mostradas.  
  
 /Current  
 Opcional. Mostra a linha atual.  
  
 /File:`filename`  
 Opcional. Caminho do arquivo a ser exibido. Se nenhum nome de arquivo for especificado, o comando mostrará o código-fonte da linha da instrução atual.  
  
 /Line:`number`  
 Opcional. Mostra um número de linha específico.  
  
 /ShowLineNumbers:`yes|no`  
 Opcional. Especifica se os números de linha devem ser exibidos.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 Este exemplo lista o código-fonte da linha 4 do arquivo Form1.vb, com números de linha visíveis.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)
