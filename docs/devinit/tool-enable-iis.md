---
title: enable-iis
description: ferramenta devinit Enable-IIS.
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
ms.openlocfilehash: 3324cf5faa1d9385adbbdf24a8125970c5db2c40
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862238"
---
# <a name="enable-iis"></a>enable-iis

A `enable-iis` ferramenta é usada para habilitar recursos do IIS e instalar o [módulo ASP.NET Core](/aspnet/core/host-and-deploy/aspnet-core-module) para desenvolvimento ASP.NET com o IIS.

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                               |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado.                                                                           |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado.                                                                           |

### <a name="input"></a>Entrada

Não usado.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `enable-iis` ferramenta é habilitar os recursos do IIS: IIS-WebServer, IIS-WebServerRole, IIS-WebSockets e IIS-webauthentication e, em seguida, instalar a versão mais recente do pacote de hospedagem do ASP.NET que inclui o módulo ASP.NET Core. 

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```