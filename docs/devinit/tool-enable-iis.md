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
ms.openlocfilehash: ec326871f5565ecaabdc8cda369b36df14029414
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399826"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```