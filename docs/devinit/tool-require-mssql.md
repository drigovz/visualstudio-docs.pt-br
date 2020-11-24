---
title: require-mssql
description: ferramenta devinit require-MSSQL.
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
ms.openlocfilehash: 95558da015462899d0388870fce95d19030fc291
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442094"
---
# <a name="require-mssql"></a>require-mssql

A `require-mssql` ferramenta é usada para instalar o [Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) por meio do ISO do MS SQL Server. O SQL Server estará disponível no `localhost` uso da autenticação integrada do Windows. o SQL Server será acessível com a cadeia de conexão `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                   |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Consulte a [entrada](#input) abaixo para obter detalhes.                                                  |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.              |

### <a name="input"></a>Entrada

A `input` propriedade pode ser uma cadeia de caracteres com um dos dois valores:

| Valor     | Descrição                              |
|-----------|------------------------------------------|
| instalar   | Instala o SQL Server.                     |
| uninstall | Desinstala todas as instalações do SQL Server. |

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-mssql` ferramenta é instalar o SQL Server.

### <a name="built-in-options"></a>Opções internas

A `require-mssql` ferramenta define um número de argumentos de linha de comando do instalador para garantir que o instalador possa ser executado sem periféricos. Esses argumentos estão listados abaixo e a documentação sobre eles pode ser encontrada na [documentação de instalação do SQL](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true).

| Nome                                                               | Descrição |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION = instalar                                                    |             |
| /FEATURES = SQLEngine, LocalDB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = false                                                         |             |
| /INSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Arquivos de Programas\microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Arquivos de programas (x86) \Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT = true                                        |             |
| /INSTANCEDIR = "C:\Arquivos de Programas\microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = manual                                          |             |
| /SQLSVCSTARTUPTYPE = automático                                       |             |
| /SQLCOLLATION = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS = administradores                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `require-msssql` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.js, que instalará o MSSQL:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```