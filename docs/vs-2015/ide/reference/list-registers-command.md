---
title: Comando Listar Registros | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6fadd5429b351eb2393aa0823dec133749b32c83
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763031"
---
# <a name="list-registers-command"></a>Comando Listar Registros
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Exibe o valor dos registros selecionados e permite modificar a lista de registros a mostrar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Opções  
 /Display [{`register`&#124;`registerGroup`}...]  
 Exibe os valores do `register` ou `registerGroup` especificado. Se nenhum `register` ou `registerGroup` for especificado, a lista padrão de registros será exibida. Se nenhuma opção for especificada, o comportamento será o mesmo. Por exemplo:  
  
 `Debug.ListRegisters /Display eax`  
  
 equivale a  
  
 `Debug.ListRegisters eax`  
  
 /List  
 Exibe todos os grupos de registros na lista.  
  
 /Watch [{`register`&#124;`registerGroup`}...]  
 Adiciona um ou mais valores `register` ou `registerGroup` à lista.  
  
 /Unwatch [{`register`&#124;`registerGroup`}...]  
 Remove um ou mais valores `register` ou `registerGroup` da lista.  
  
## <a name="remarks"></a>Comentários  
 O alias `r` pode ser usado no lugar de `Debug.ListRegisters`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o alias `Debug.ListRegisters` `r` para exibir os valores do registro de grupo `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Noções básicas sobre depuração: janela Registros](../../debugger/debugging-basics-registers-window.md)   
 [Como usar a janela Registros](../../debugger/how-to-use-the-registers-window.md)
