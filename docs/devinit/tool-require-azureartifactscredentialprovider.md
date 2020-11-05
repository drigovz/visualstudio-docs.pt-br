---
title: require-azureartifactscredentialprovider
description: a ferramenta devinit requer-azureartifactscredentialprovider.
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
ms.openlocfilehash: c784bb25fe9abc77cfb562ae085930b275d0ef03
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400284"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

A `require-azureartifactscredentialprovider` ferramenta instala o provedor de credenciais Azure Artifacts. O provedor de credenciais Azure Artifacts automatiza a aquisição de credenciais necessárias para restaurar os pacotes NuGet como parte do seu fluxo de trabalho de desenvolvimento do .NET. Leia mais sobre Azure Artifacts provedor de credenciais [aqui](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado. Consulte a [entrada](#input) abaixo para obter detalhes. |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.                     |

### <a name="input"></a>Entrada

Não usado. Ignora qualquer entrada, se mencionada.

### <a name="additional-options"></a>Opções adicionais

As opções adicionais são passadas como estão para o comando do provedor de credenciais.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-azureartifactscredentialprovider` ferramenta é instalar o mais recente de Azure Artifacts provedor de credenciais.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file that installs Azure Artifacts Credential Provider.'",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
            "comments": "Installs Azure Artifacts Credential Provider."
        }
    ]
}
```
