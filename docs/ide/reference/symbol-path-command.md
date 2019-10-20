---
title: Comando demarcador do Símbolo
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6309396877a32233bfe05fff1d2173d1f8765ebb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645192"
---
# <a name="symbol-path-command"></a>Comando demarcador do Símbolo
Define a lista de diretórios para o depurador pesquisar símbolos.

## <a name="syntax"></a>Sintaxe

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
`pathname`

Opcional. Uma lista de caminhos delimitada por ponto-e-vírgula para que o depurador pesquise símbolos.

## <a name="remarks"></a>Comentários
Se nenhum `pathname` for especificado, o comando listará os caminhos de símbolo atual.

## <a name="example"></a>Exemplo
Este exemplo adiciona dois caminhos à lista de diretórios de símbolo.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Exemplo
Este exemplo exibe uma lista delimitada por ponto-e-vírgula dos caminhos de símbolo atuais.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Consulte também

- [Janela Comando](../../ide/reference/command-window.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)