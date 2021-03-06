---
title: Arquivo de configuração devinit
description: Documentação para o .devinit.jsno arquivo de manifesto para devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 47859d00861c2361ed03931bf1417e22425d6e68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908117"
---
# <a name="devinit-configuration-file"></a>arquivo de configuração devinit

O `.devinit.json` arquivo define as dependências de todo o sistema de que seu aplicativo precisa para executar e compilar. As dependências de todo o sistema são coisas como Node.js, SQL Server, IIS, RabbitMQ, Docker etc. Esses são os tipos de coisas que você normalmente instalaria em sua caixa de desenvolvimento que não estão instaladas por um repositório específico. Não é um local para definir dependências específicas do aplicativo, como você faria em gerenciadores de pacotes, como NuGet ou NPM. No entanto, é um local para definir que você precisa desses gerenciadores de pacotes.

## <a name="file-location"></a>Local do arquivo

O `devinit init` comando é controlado por meio do `.devinit.json` arquivo. Por padrão, `devinit` o procura o arquivo nos seguintes locais:

* {diretório atual} \\.devinit.jsem
* {diretório atual} \\devinit.jsem
* {diretório atual} \\ . devinit \\.devinit.jsem
* {diretório atual} \\ . devinit \\devinit.jsem
* {diretório atual} \\ devinit \\.devinit.jsem
* {diretório atual} \\ devinit \\devinit.jsem
* {diretório atual} \\ . devcontainer \\.devinit.jsem
* {diretório atual} \\ . devcontainer \\devinit.jsem

> [!NOTE]
> Se vários arquivos padrão forem encontrados, o devinit usará o arquivo que aparece primeiro na lista acima.

O `.devinit.json` arquivo também pode ser especificado explicitamente por meio da `--file` / `-f` opção.

### <a name="directories-and-relative-paths"></a>Diretórios e caminhos relativos

Os caminhos são relativos ao local onde devinit está em execução. Normalmente, esse é o diretório de trabalho atual do qual `devinit` foi executado.

## <a name="file-format"></a>Formato de arquivo
Em um `.devinit.json` , você pode especificar mais de uma ferramenta a ser executada. Na `run` seção, você pode colocar qualquer número de objetos. Um exemplo disso é visto em nosso exemplo [.devinit.js](sample-all-tool.md) com todas as nossas ferramentas.

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Valores de propriedade

| Nome         | Tipo   | Obrigatório | Valor                              |
|--------------|--------|----------|------------------------------------|
| **feitos** | Cadeia de caracteres | No       | Comentários para o arquivo.             |
| **funcionam**      | array  | Sim      | [Objeto RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Executar objeto de ferramenta

| Nome                  | Tipo   | Obrigatório | Valor                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **feitos**          | Cadeia de caracteres | No       | Comentários para a entrada da ferramenta.                                                                               |
| **'**              | string | Sim      | O nome da ferramenta. Consulte o `devinit list` comando para obter uma lista de ferramentas disponíveis.                            |
| **input**             | Cadeia de caracteres | No       | A entrada da ferramenta. Varia de acordo com a ferramenta. Por exemplo, a versão necessária, a ID do pacote, o nome do arquivo ou a pasta.|
| **additionalOptions** | Cadeia de caracteres | No       | Argumentos de linha de comando adicionais a serem passados para a ferramenta.                                                |

## <a name="examples"></a>Exemplos

Para obter mais exemplos de como usar o devinit, consulte a [seção de exemplos](sample-readme.md).
