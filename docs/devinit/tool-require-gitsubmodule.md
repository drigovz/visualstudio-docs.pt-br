---
title: exigir-gitsubmodule
description: a ferramenta devinit requer-gitsubmodule.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: fc96c1d0bf278018c370795d6ad5f9d22cb59bcc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810126"
---
# <a name="require-gitsubmodule"></a>exigir-gitsubmodule

A `require-gitsubmodule` ferramenta restaura submódulos git para determinado `.gitmodules` arquivo. Usa o `.gitmodules` arquivo local no diretório raiz se nenhuma entrada for passada. Leia mais sobre os submódulos do git [aqui](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | `.gitmodules` caminho completo do arquivo. Consulte a [entrada](#input) abaixo para obter detalhes.               |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.                     |

### <a name="input"></a>Entrada

Opcional, `input` é usado para obter o `.gitmodules` caminho do arquivo para restauração. Se `input` for omitido, o arquivo do diretório raiz `.gitmodules` será usado.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-gitsubmodule` ferramenta é restaurar os submódulos git mencionados no `.gitmodules` arquivo.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores Git submodules.'",
    "run": [
        {
            "tool": "require-gitsubmodule",
            "input": "RepoThatHasDotGitModulesFile",
            "comments": "Input specifies a folder that contains a .gitmodules file. If no input is specified, then current directory is used."
        }
    ]
}
```
