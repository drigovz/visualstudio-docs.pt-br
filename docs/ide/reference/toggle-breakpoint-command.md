---
title: Comando Ativar/Desativar Ponto de Interrupção
description: Saiba como usar o comando Alternar ponto de interrupção para ativar ou desativar o ponto de interrupção, dependendo de seu estado atual, no local atual do arquivo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b65144271f91d518dd6649fa1e97fc627d1b0009
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560961"
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
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
