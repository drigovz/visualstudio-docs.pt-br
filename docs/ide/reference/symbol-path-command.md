---
title: Comando demarcador do Símbolo
description: Saiba mais sobre o comando de caminho de símbolo e como ele define a lista de diretórios para o depurador procurar por símbolos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 72e69300e9dc621ea346c05923168c33bc7065c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967157"
---
# <a name="symbol-path-command"></a>Comando demarcador do Símbolo
Define a lista de diretórios para o depurador pesquisar símbolos.

## <a name="syntax"></a>Sintaxe

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumentos
`pathname`

Opcional. Uma lista de caminhos delimitada por ponto-e-vírgula para que o depurador pesquise símbolos.

## <a name="remarks"></a>Comentários
Se nenhum `pathname` for especificado, o comando listará os caminhos de símbolo atual.

## <a name="example-1"></a>Exemplo 1
Este exemplo adiciona dois caminhos à lista de diretórios de símbolo.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Exemplo 2
Este exemplo exibe uma lista delimitada por ponto-e-vírgula dos caminhos de símbolo atuais.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Confira também

- [Janela de comando](../../ide/reference/command-window.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
