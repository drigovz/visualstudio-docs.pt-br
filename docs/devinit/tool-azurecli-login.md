---
title: azurecli-login
description: devinit Tool azurecli-login.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 94f713ed972e93b761cf7dcdafcfd92e5498d982
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944967"
---
# <a name="azurecli-login"></a>azurecli-login

A `azurecli-login` ferramenta é usada para entrar Azure Active Directory via [CLI do Azure](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest). Essa ferramenta usa o comando CLI do Azure: `az login --use-device-code` , para concluir o logon, você precisará seguir as instruções impressas no console.

## <a name="usage"></a>Uso

Se ambas as propriedades forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                          |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado. Consulte a [entrada](#input) abaixo para obter detalhes.                               |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.     |

### <a name="input"></a>Entrada

Não usado.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `azurecli-login` ferramenta é instalar a versão mais recente do CLI do Azure e adicioná-la ao `PATH` .

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `azurecli-login` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-trigger-azure-login"></a>.devinit.jsno que irá disparar o logon do Azure:

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "azurecli-login"
        }
    ]
}
```