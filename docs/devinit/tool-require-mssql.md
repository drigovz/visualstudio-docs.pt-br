---
title: require-mssql
description: ferramenta devinit require-MSSQL.
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
ms.openlocfilehash: 2ad02a29b8ea8b59abd4f246c5cc1d206451d3fc
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005186"
---
# <a name="require-mssql"></a>require-mssql

A `require-mssql` ferramenta é usada para instalar o [Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) por meio do ISO do MS SQL Server. O SQL Server estará disponível no `localhost` uso da autenticação integrada do Windows. o SQL Server será acessível com a cadeia de conexão `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                   |
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

### <a name="builtin-options"></a>Opções internas

A `require-mssql` ferramenta define um número de argumentos de linha de comando do instalador para garantir que o instalador possa ser executado sem periféricos. Esses argumentos estão listados abaixo e a documentação sobre eles pode ser encontrada na [documentação de instalação do SQL](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true).

| Name                                                               | Descrição |
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs MSSQL.",
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```
