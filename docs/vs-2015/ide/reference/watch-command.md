---
title: Comando de Inspeção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604830"
---
# <a name="watch-command"></a>Comando Inspecionar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cria e abre uma instância especificada de uma janela **Inspeção**. Você pode usar uma janela **Inspeção** para calcular os valores de variáveis, expressões e registros, para editar esses valores e para salvar os resultados.

## <a name="syntax"></a>Sintaxe

```
Debug.Watch[index]
```

## <a name="arguments"></a>Arguments
 `index` Necessário. O número de instância da janela Inspeção.

## <a name="remarks"></a>Comentários
 O `index` deve ser um inteiro. Os valores válidos são 1, 2, 3 ou 4.

## <a name="example"></a>Exemplo

```
>Debug.Watch1
```

## <a name="see-also"></a>Veja também
 [As janelas automáticas e locais ](../../debugger/autos-and-locals-windows.md) [How para: editar um valor em uma janela de variável ](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [How para: Use a caixa de diálogo QuickWatch ](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) comandos do [Visual Studio ](../../ide/reference/visual-studio-commands.md) janela do [Command ](../../ide/reference/command-window.md) caixa de/Command [Find 10 aliases de comando do](../../ide/find-command-box.md) [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
