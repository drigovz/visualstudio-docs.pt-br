---
title: azurecli-login
description: devinit Tool azurecli-login.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 86427e0ad6dde2f51336d9ea0e508413425fdc29
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399656"
---
# <a name="azurecli-login"></a>azurecli-login

A `azurecli-login` ferramenta é usada para entrar Azure Active Directory via [CLI do Azure](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest). Essa ferramenta usa o comando CLI do Azure: `az login --use-device-code` , para concluir o logon, você precisará seguir as instruções impressas no console.

## <a name="usage"></a>Uso

Se ambas as propriedades forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                          |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado. Consulte a [entrada](#input) abaixo para obter detalhes.                               |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.     |

### <a name="input"></a>Entrada

Não usado.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `azurecli-login` ferramenta é instalar a versão mais recente do CLI do Azure e adicioná-la ao caminho (somente Windows).

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger az login --use-device-code behavior.",
            "tool": "azurecli-login"
        }
    ]
}
```