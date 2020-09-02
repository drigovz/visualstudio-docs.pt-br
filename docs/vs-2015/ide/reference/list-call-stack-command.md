---
title: Comando Listar Pilha de Chamadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c44ac18468fbd26adab2cf973a21df58ebb28c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657656"
---
# <a name="list-call-stack-command"></a>Comando Listar Pilha de Chamadas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exibe a pilha de chamadas atual.

## <a name="syntax"></a>Sintaxe

```
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Argumentos
 `index` Opcional. Define o registro de ativação atual e não exibe nenhuma saída.

## <a name="switches"></a>Comutadores
 Cada opção pode ser invocada usando sua forma completa ou abreviada.

 /Count: `number` [ou]/c: `number` opcional. Número máximo de pilhas de chamadas a exibir. O valor padrão é ilimitado.

 /ShowTypes: `yes`&#124;`no` [ou]/t: `yes`&#124;`no` opcional. Especifica se deve tipos de parâmetro devem ser exibidos. O valor padrão é `yes`.

 /ShowNames: `yes`&#124;`no` [ou]/n: `yes`&#124;`no` opcional. Especifica se nomes de parâmetro devem ser exibidos. O valor padrão é `yes`.

 /ShowValues: `yes`&#124;`no` [ou]/v: `yes`&#124;`no` opcional. Especifica se valores de parâmetro devem ser exibidos. O valor padrão é `yes`.

 /ShowModule: `yes`&#124;`no` [ou]/m: `yes`&#124;`no` opcional. Especifica se deve o nome do módulo deve ser exibido. O valor padrão é `yes`.

 /ShowLineOffset: `yes`&#124;`no` [ou]/#: `yes`&#124;`no` opcional. Especifica se o deslocamento de linha deve ser exibido. O valor padrão é `no`.

 /ShowByteOffset: `yes`&#124;`no` [ou]/b: `yes`&#124;`no` opcional. Especifica se o deslocamento de byte deve ser exibido. O valor padrão é `no`.

 /ShowLanguage: `yes`&#124;`no` [ou]/l: `yes`&#124;`no` opcional. Especifica se o idioma deve ser exibido. O valor padrão é `no`.

 /IncludeCallsAcrossThreads: `yes`&#124;`no` [ou]/i: `yes`&#124;`no` opcional. Especifica se chamadas de ou para outros threads devem ser incluídas. O valor padrão é `no`.

 /ShowExternalCode: `yes`&#124;`no` opcional. Especifica se Apenas Meu Código deve ser exibido para a pilha de chamadas. Quando Apenas Meu Código está desativado, todo o código não do usuário é exibido. Quando Apenas Meu Código está ativado, o código não do usuário é exibido como `[external]` na saída da pilha de chamadas.

 Thread: `n` opcional. exibe a pilha de chamadas para o thread `n`. Se nenhum thread for especificado, exibirá a pilha de chamadas do thread atual.

## <a name="remarks"></a>Comentários
 As alterações feitas a argumentos ou opções aplicam-se a invocações futuras desse comando. Se você emitir Debug.ListCallStackby em si, toda a pilha de chamadas será exibida. Se você especificar um índice, por exemplo,

```
Debug.ListCallStack 2
```

 o registro de ativação atual será definido como aquele quadro (neste caso, o segundo quadro).

 Você também pode escrever esse comando usando seu alias predefinido, kb. Por exemplo, você pode inserir

```
kb 2
```

 para definir o registro de ativação atual para o segundo quadro.

## <a name="example"></a>Exemplo

```
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Consulte Também
 [Listar](../../ide/reference/list-disassembly-command.md) os [threads da lista](../../ide/reference/list-threads-command.md) de comandos de desmontagem do [Visual Studio comandos](../../ide/reference/visual-studio-commands.md) da [janela](../../ide/reference/command-window.md) de comando [Localizar/comandos caixa de comando](../../ide/find-command-box.md) do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
