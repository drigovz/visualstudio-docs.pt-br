---
title: Comando Iniciar
description: Saiba mais sobre o comando Iniciar e como ele começa a depurar o projeto de inicialização.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6d9e1e36a2790fb63f9d39c0c83d67d889cc0a8
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616415"
---
# <a name="start-command"></a>Comando Iniciar
Inicia a depuração do projeto de inicialização.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumentos
`address`

Opcional. O endereço no qual o programa suspende a execução, semelhante a um ponto de interrupção no código-fonte. Este argumento é válido apenas no modo de depuração.

## <a name="remarks"></a>Comentários
O comando **Iniciar**, quando executado, executa uma operação RunToCursor para o endereço especificado.

## <a name="example"></a>Exemplo
Este exemplo inicia o depurador e ignora todas as exceções que ocorrerem.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
