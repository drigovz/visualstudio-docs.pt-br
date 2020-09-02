---
title: Comando Iniciar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663490"
---
# <a name="start-command"></a>Comando Iniciar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inicia a depuração do projeto de inicialização.

## <a name="syntax"></a>Sintaxe

```
Debug.Start [address]
```

## <a name="arguments"></a>Argumentos
 `address` Opcional. O endereço no qual o programa suspende a execução, semelhante a um ponto de interrupção no código-fonte. Este argumento é válido apenas no modo de depuração.

## <a name="remarks"></a>Comentários
 O comando **Iniciar**, quando executado, executa uma operação RunToCursor para o endereço especificado.

## <a name="example"></a>Exemplo
 Este exemplo inicia o depurador e ignora todas as exceções que ocorrerem.

```
>Debug.Start
```

## <a name="see-also"></a>Consulte Também
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela](../../ide/reference/command-window.md) de comando [Localizar/comando caixa](../../ide/find-command-box.md) de comandos do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
