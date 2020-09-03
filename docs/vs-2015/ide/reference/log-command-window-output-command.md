---
title: Comando Log Command Window Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666862"
---
# <a name="log-command-window-output-command"></a>Comando Saída da Janela Log de Comando
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Copia todas as entradas e saídas da janela de **comando** em um arquivo.

## <a name="syntax"></a>Sintaxe

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumentos
 `filename` Opcional. O nome do arquivo de log. Por padrão, o arquivo é criado na pasta de perfil do usuário. Se o nome do arquivo já existir, o log será acrescentado ao final do arquivo existente. Se nenhum arquivo for especificado, o último arquivo especificado será usado. Não se houver nenhum arquivo anterior, será criado um arquivo de log padrão, chamado cmdline.log.

> [!TIP]
> Para alterar o local em que o arquivo de log é salvo, digite o caminho completo do arquivo entre aspas se o caminho contiver espaços.

## <a name="switches"></a>Comutadores
 /on opcional. Inicia o log para a janela **Comando** no arquivo especificado e anexa o arquivo com as novas informações.

 /off opcional. Parar o log para a janela **Comando**.

 /overwrite opcional. Se o arquivo especificado no argumento `filename` corresponder a um arquivo existente, o arquivo será substituído.

## <a name="remarks"></a>Comentários
 Se nenhum arquivo for especificado, o arquivo cmdline.log será criado por padrão. Por padrão, o alias para esse comando é Log.

## <a name="examples"></a>Exemplos
 Este exemplo cria um novo arquivo de log, cmdlog, e inicia o log de comando.

```
>Tools.LogCommandWindowOutput cmdlog
```

 Este exemplo interrompe os comandos de log.

```
>Tools.LogCommandWindowOutput /off
```

 Este exemplo retoma o log de comandos no arquivo de log usado anteriormente.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Consulte Também
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela](../../ide/reference/command-window.md) de comando [Localizar/comando caixa](../../ide/find-command-box.md) de comandos do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
