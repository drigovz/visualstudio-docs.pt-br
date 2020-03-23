---
title: Comando Ativar/Desativar Ponto de Interrupção
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d393890e6166b4a4ef53c9520a556e9a9edd64d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597315"
---
# <a name="toggle-breakpoint-command"></a>Comando Ativar/Desativar Ponto de Interrupção
Ativa ou desativa o ponto de interrupção dependendo de seu estado atual, no local atual do arquivo.

## <a name="syntax"></a>Sintaxe

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumentos

`text`\
Opcional. Se o texto for especificado, a linha será marcada como um ponto de interrupção nomeado. Caso contrário, a linha será marcada como um ponto de interrupção sem nome, semelhante ao que acontece quando você pressiona F9.

## <a name="example"></a>Exemplo
O exemplo a seguir ativa/desativa o ponto de interrupção atual.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
