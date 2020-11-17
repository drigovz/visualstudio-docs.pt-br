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
ms.openlocfilehash: 0aa0d250289e6bf79467c0a00ddddef5264ed6d2
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671895"
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
Veja abaixo um exemplo de como executar `require-azureartifactscredentialprovider` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.js, que instalará Azure Artifacts provedor de credenciais:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
