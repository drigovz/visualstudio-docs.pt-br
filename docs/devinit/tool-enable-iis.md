---
title: enable-iis
description: ferramenta devinit Enable-IIS.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b4b7c3f9681dd636ef88a5cd9f59c84c4ecac89c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440357"
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