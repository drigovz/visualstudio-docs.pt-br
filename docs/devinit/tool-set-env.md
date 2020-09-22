---
title: set-env
description: ferramenta devinit require-Set-env.
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
ms.openlocfilehash: 2f4ec5489f22e94ad8f57f22ddc7742dc0ae3ade
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005991"
---
# <a name="set-env"></a>set-env

A `set-env` ferramenta pode ser usada para definir variáveis de ambiente para uso no processo atual. As variáveis de ambiente são definidas somente no processo atual e serão usadas por outras `devinit` ferramentas se elas forem executadas nesse processo.

Essa ferramenta utiliza a API do .NET Core `Environment.SetEnvironment` e tem as mesmas limitações que essa API. Para obter mais informações, consulte a [documentação](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) do `Environment.SetEnvironment` .

## <a name="usage"></a>Uso

| Nome                                         | Tipo   | Obrigatório | Valor                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **feitos**                                 | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                       |
| [**entrada**](#input)                          | Cadeia de caracteres | No       | A entrada para a ferramenta. Consulte a [entrada](#input) abaixo para obter detalhes.               |
| [**additionalOptions**](#additional-options) | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.  |

### <a name="input"></a>Entrada

A `set-env` ferramenta usa uma única cadeia de caracteres como uma entrada na `input` propriedade. A cadeia de caracteres deve ser formatada como uma cadeia de caracteres de ponto e vírgula (;) pares delimitados de valor de chave (nome = valor) e quatro ações possíveis com base no valor da `input` propriedade.

| Ação       | Entrada            | Descrição                                                                                                                                                              | Exemplo             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **list all** | vazio ou omitido | Listar todas as variáveis de ambiente atuais.                                                                                                                              | `"input":""`        |
| **listar um** | string           | Liste o valor de uma variável de ambiente específica por nome.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Define o valor de uma variável de ambiente como par chave-valor. Adiciona uma nova variável de ambiente, se ainda não estiver presente, ou definir o valor de uma variável de ambiente existente | `"input":"foo=bar"` |
| **delete**   | string           | Exclui uma variável de ambiente existente passando uma cadeia de caracteres de valor vazia.                                                                                            | `"input":"foo="`    |

Uma `input` cadeia de caracteres pode conter uma expansão de variável de ambiente, por exemplo `%userprofile%` , que é expandida quando o valor é lido.

### <a name="additional-options"></a>Opções adicionais

Não usado.

## <a name="usage-in-a-codespace"></a>Uso em um codespace

Se você estiver usando um codespace, poderá definir as variáveis de ambiente usadas no codespace até Customizating a `remoteEnv` propriedade no [`.devcontainer.json`](https://docs.microsoft.com/visualstudio/codespaces/reference/configuring) arquivo.

## <a name="example-usage"></a>Exemplo de uso

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "comments": "A sample dot-devinit file demonstrating the set-env tool.",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "comments": "To set an environment variable, set input to 'name=value'."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "To display the value of a single environment variable, set input to the name of the variable."
    },
    {
      "tool": "set-env",
      "comments": "To list all environment variables, pass no input."
    },
    {
      "tool": "set-env",
      "input": "foo=",
      "comments": "To delete an environment variable, pass input of 'name='."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "Trying to display a variable that doesn't exist results in a warning."
    },
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
      "comments": "Envrionment variable expansion is supported."
    },
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
      "comments": "Shows path manipulation. Note: Variables set here are not persisted."
    },
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
      "comments": "Restore path from saved copy."
    }
  ]
}
```
