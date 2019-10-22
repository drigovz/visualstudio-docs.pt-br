---
title: Comando Listar Módulos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659528"
---
# <a name="list-modules-command"></a>Comando Listar Módulos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lista os módulos do processo atual.

## <a name="syntax"></a>Sintaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parâmetros
 /Address: `yes|no` opcional. Especifica se os endereços de memória dos módulos devem ser exibidos. O valor padrão é `yes`.

 /Name:`yes|no` opcional. Especifica se os nomes dos módulos devem ser exibidos. O valor padrão é `yes`.

 /Order: `yes|no` opcional. Especifica se a ordem dos módulos deve ser exibida. O valor padrão é `no`.

 /Path:`yes|no` opcional. Especifica se os caminhos dos módulos devem ser exibidos. O valor padrão é `yes`.

 /Process: `yes|no` opcional. Especifica se os processos dos módulos devem ser exibidos. O valor padrão é `no`.

 /SymbolFile: `yes|no` opcional. Especifica se os arquivos de símbolo dos módulos devem ser exibidos. O valor padrão é `no`.

 /SymbolStatus: `yes|no` opcional. Especifica se os status de símbolo dos módulos devem ser exibidos. O valor padrão é `yes`.

 /Timestamp: `yes|no` opcional. Especifica se os carimbos de data/hora dos módulos devem ser exibidos. O valor padrão é `no`.

 /Version: `yes|no` opcional. Especifica se as versões dos módulos devem ser exibidas. O valor padrão é `no`.

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 Este exemplo lista os nomes, endereços e carimbos de data/hora do módulo para o processo atual.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Veja também
 [Janela de comando](../../ide/reference/command-window.md) de [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [como: usar a janela de módulos](../../debugger/how-to-use-the-modules-window.md)
