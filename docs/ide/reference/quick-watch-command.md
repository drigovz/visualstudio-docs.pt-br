---
title: Comando Inspeção Rápida
description: Saiba mais sobre o comando de inspeção rápida e como ele exibe o texto selecionado ou especificado no campo expressão da janela QuickWatch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5557fb9ca4c362f764cac04441add4fea0433856
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958187"
---
# <a name="quick-watch-command"></a>Comando Inspeção Rápida
Exibe o texto selecionado ou especificado no campo Expressão da janela [QuickWatch](../../debugger/watch-and-quickwatch-windows.md). Você pode usar essa caixa de diálogo para calcular o valor atual de uma variável ou expressão reconhecida pelo depurador ou o conteúdo de um registro. Além disso, você pode alterar o valor de qualquer variável não const ou o conteúdo de qualquer registro.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumentos

`text`\
Opcional. O texto a ser adicionado à caixa de diálogo **Inspeção Rápida**.

## <a name="remarks"></a>Comentários

Se `text` for omitido, o texto selecionado atualmente ou a palavra no cursor é adicionada à janela Inspeção.

## <a name="example"></a>Exemplo

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Confira também

- [Definir uma inspeção nas variáveis usando as janelas Inspeção e QuickWatch no Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
