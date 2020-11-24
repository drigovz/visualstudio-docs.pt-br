---
title: set-env
description: ferramenta devinit require-Set-env.
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
ms.openlocfilehash: 820cd87f26e4babc7a83d975c3fb480187af564f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442280"
---
# <a name="set-env"></a>set-env

A `set-env` ferramenta pode ser usada para definir variáveis de ambiente para uso no processo atual. As variáveis de ambiente são definidas somente no processo atual e serão usadas por outras `devinit` ferramentas se elas forem executadas nesse processo.

Essa ferramenta utiliza a API do .NET Core `Environment.SetEnvironment` e tem as mesmas limitações que essa API. Para obter mais informações, consulte a [documentação](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) do `Environment.SetEnvironment` .

## <a name="usage"></a>Uso

| Nome                                         | Type   | Obrigatório | Valor                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **feitos**                                 | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                       |
| [**entrada**](#input)                          | Cadeia de caracteres | No       | A entrada para a ferramenta. Consulte a [entrada](#input) abaixo para obter detalhes.               |
| [**additionalOptions**](#additional-options) | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.  |

### <a name="input"></a>Entrada

A `set-env` ferramenta usa uma única cadeia de caracteres como uma entrada na `input` propriedade. A cadeia de caracteres deve ser formatada como uma cadeia de caracteres de ponto e vírgula (;) pares delimitados de valor de chave (nome = valor) e quatro ações possíveis com base no valor da `input` propriedade.

| Ação       | Entrada            | Descrição                                                                                                                                                              | Exemplo             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **list all** | vazio ou omitido | Listar todas as variáveis de ambiente atuais.                                                                                                                           | `"input":""`        |
| **listar um** | string           | Liste o valor de uma variável de ambiente específica por nome.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Define o valor de uma variável de ambiente como par chave-valor. Adiciona uma nova variável de ambiente, se ainda não estiver presente, ou definir o valor de uma variável de ambiente existente | `"input":"foo=bar"` |
| **delete**   | string           | Exclui uma variável de ambiente existente passando uma cadeia de caracteres de valor vazia.                                                                                            | `"input":"foo="`    |

Uma `input` cadeia de caracteres pode conter uma expansão de variável de ambiente, por exemplo `%userprofile%` , que é expandida quando o valor é lido.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `set-env` ferramenta é listar todas as variáveis de ambiente atuais.

## <a name="usage-in-a-codespace"></a>Uso em um codespace

Se você estiver usando um codespace, poderá definir as variáveis de ambiente usadas no codespace por meio da personalização da `remoteEnv` propriedade no [`.devcontainer.json`](/visualstudio/codespaces/reference/configuring) arquivo.

## <a name="example-usage"></a>Exemplo de uso
Abaixo estão exemplos de como executar `set-env` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.jsno que definirá uma variável de ambiente, `foo` , para value, `bar` :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
    }
  ]
}
```

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.js, que exibirá o valor de uma variável de ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo",
    }
  ]
}
```

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>.devinit.js, que listará todas as variáveis de ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
    }
  ]
}
```

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>.devinit.js, que excluirá uma variável de ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=",
    }
  ]
}
```


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>.devinit.jsque usarão a expansão da variável de ambiente:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.js, que definirá um valor de variável de ambiente usando a manipulação de caminho:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
    }
  ]
}
```

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.jsno que irá restaurar o caminho da cópia salva:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
    }
  ]
}
```
