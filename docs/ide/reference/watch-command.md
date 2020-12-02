---
title: Comando Inspecionar
description: Saiba mais sobre o comando Watch e como ele cria e abre uma instância especificada de um janela Inspeção.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631c9cf61e6da70b3c7554a1aac0cacc8eef0294
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480142"
---
# <a name="watch-command"></a>Comando Inspecionar
Cria e abre uma instância especificada de uma janela **Inspeção**. Você pode usar uma janela **Inspeção** para calcular os valores de variáveis, expressões e registros, para editar esses valores e para salvar os resultados.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumentos

`index`\
Obrigatórios. O número de instância da janela Inspeção.

## <a name="remarks"></a>Comentários

O `index` deve ser um inteiro. Os valores válidos são 1, 2, 3 ou 4.

## <a name="example"></a>Exemplo

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Confira também

- [Janelas autos e locais](../../debugger/autos-and-locals-windows.md)
- [Definir uma inspeção nas variáveis usando as janelas Inspeção e QuickWatch no Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
