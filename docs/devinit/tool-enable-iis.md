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
ms.openlocfilehash: 9b6ba2e22484850dd6079cfc7e4ab9cd68371dcb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671922"
---
# <a name="enable-iis"></a>enable-iis

A `enable-iis` ferramenta é usada para habilitar recursos do IIS e instalar o [módulo ASP.NET Core](/aspnet/core/host-and-deploy/aspnet-core-module) para desenvolvimento ASP.NET com o IIS.

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                               |
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
Veja abaixo um exemplo de como executar `enable-iis` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.jsno que permitirá o desenvolvimento do IIS:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "enable-iis"
        },
    ]
}
```