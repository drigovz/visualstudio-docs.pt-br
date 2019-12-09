---
title: Convenções de nomenclatura do .NET para arquivos EditorConfig
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ff6c9885bd01a94cc36046faf71067e1fe9c17b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650909"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Convenções de nomenclatura do .NET para EditorConfig

As convenções de nomenclatura referem-se à nomenclatura dos elementos de código, como classes, propriedades e métodos. Por exemplo, é possível especificar que membros públicos devem ser escritos em maiúsculas ou que métodos assíncronos devem terminar com "Async". É possível aplicar essas regras especificando-as em um [arquivo .editorconfig](../ide/create-portable-custom-editor-options.md). Violações de regras de nomenclatura são exibidas na **Lista de Erros** ou como uma sugestão embaixo do nome, dependendo da gravidade escolhida para a regra. Não é necessário criar o projeto para ver as violações.

Para cada convenção de nomenclatura, é necessário especificar os símbolos aos quais ela se aplica, um estilo de nomenclatura e uma gravidade para impor a convenção, usando as propriedades descritas abaixo. A ordem das propriedades não é importante.

Para começar, escolha um título para a regra de nomenclatura que será usada em cada uma das propriedades necessárias para descrever completamente a regra. Por exemplo, `public_members_must_be_capitalized` é um nome bom e descritivo para uma regra de nomenclatura. Esta página vai se referir ao título escolhido como **<namingRuleTitle\>** nas seções a seguir.

## <a name="symbols"></a>Símbolos

Primeiro, identifique um grupo de símbolos ao qual aplicar a regra de nomenclatura. Essa propriedade tem o seguinte formato:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Dê um nome ao grupo de símbolos, substituindo o valor **<symbolTitle\>** por um título descritivo, por exemplo `public_symbols`. Você usará o valor **<symbolTitle\>** nos três nomes de propriedade que descrevem a quais símbolos a regra é aplicada (tipos de símbolo, níveis de acessibilidade e modificadores).

### <a name="kinds-of-symbols"></a>Tipos de símbolos

Para descrever o tipo de símbolos aos quais aplicar a regra de nomenclatura, especifique uma propriedade no formato a seguir:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

A lista a seguir mostra os valores permitidos e é possível especificar vários valores separando-os por vírgula.

- \* (use este valor para especificar todos os símbolos)
- namespace
- classe
- struct
- interface
- enum
- propriedade
- method
- campo
- evento
- delegado
- parâmetro
- type_parameter
- local
- local_function

### <a name="accessibility-levels-of-symbols"></a>Níveis de acessibilidade de símbolos

Para descrever os níveis de acessibilidade dos símbolos aos quais você deseja aplicar a regra de nomenclatura, especifique um nome de propriedade no formato a seguir:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

A lista a seguir mostra os valores permitidos e é possível especificar vários valores separando-os por vírgula.

- \* (use este valor para especificar todos os níveis de acessibilidade)
- públicos
- interno ou amigo
- particulares
- protegidos
- protected\_internal or protected_friend
- privado\_protegido
- local

   O nível de acessibilidade `local` se aplica a símbolos definidos em um método. É útil para definir convenções de nomenclatura para símbolos cuja acessibilidade não pode ser especificada no código. Por exemplo, se você especificar `applicable_accessibilities = local` em uma convenção de nomenclatura para constantes (`required_modifiers = const`), a regra se aplicará apenas a constantes definidas em um método e não àquelas definidas em um tipo.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Modificadores de símbolo (opcional)

Para descrever os modificadores dos símbolos aos quais você deseja aplicar a regra de nomenclatura, especifique um nome de propriedade no formato a seguir:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

A lista a seguir mostra os valores permitidos (separe vários valores por vírgula):

- `abstract` ou `must_inherit`
- `async`
- `const`
- `readonly`
- `static` ou `shared`

   > [!NOTE]
   > Se você tiver uma regra de nomenclatura para os símbolos `static` ou `shared`, ela também se aplicará aos símbolos `const` porque são implicitamente estáticos. Se não quiser que a regra de nomenclatura `static` se aplique aos símbolos `const`, crie uma regra de nomenclatura separada para os símbolos `const`.

Uma regra de nomenclatura corresponde a assinaturas que tenham *todos* os modificadores especificados em `required_modifiers`. Se você omitir essa propriedade, o valor padrão de uma lista vazia será usado, ou seja, modificadores específicos não são necessários para uma correspondência. Isso significa que os modificadores de um símbolo não têm efeito sobre a opção de aplicar essa regra ou não.

> [!TIP]
> Não especifique um valor de `*` para `required_modifiers`. Em vez disso, basta omitir totalmente a propriedade `required_modifiers` que a regra de nomenclatura será aplicada a qualquer tipo de modificador.

## <a name="style"></a>Estilo

Agora que você identificou o grupo de símbolos ao qual aplicar a regra de nomenclatura, é possível descrever o estilo de nomenclatura. Pode ser que um estilo tenha um determinado prefixo ou sufixo ou que palavras individuais no nome sejam separadas por um determinado caractere. Também é possível especificar um estilo de uso de maiúsculas. A propriedade do estilo tem o seguinte formato:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Dê um nome ao estilo substituindo o valor **<styleTitle\>** por um título descritivo, por exemplo `first_word_upper_case_style`. Use o valor **<styleTitle\>** nos nomes de propriedade que descrevem o estilo de nomenclatura (prefixo, sufixo, caractere separador de palavras e uso de maiúsculas). Use uma ou mais propriedades dessas para descrever seu estilo.

### <a name="require-a-prefix"></a>Exigir um prefixo

Para especificar que os nomes de símbolos devem começar com determinados caracteres, use esta propriedade:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Exigir um sufixo

Para especificar que os nomes de símbolos devem terminar com determinados caracteres, use esta propriedade:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Exigir um determinado separador de palavras

Para especificar que palavras individuais em nomes de símbolos devem ser separadas por um determinado caractere, use esta propriedade:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Exigir um estilo de uso de maiúsculas

Para especificar um estilo de uso de maiúsculas específico para nomes de símbolos, use esta propriedade:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Os valores permitidos para essa propriedade são:

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> É necessário especificar um estilo de uso de maiúsculas como parte do seu estilo de nomenclatura; caso contrário, o estilo de nomenclatura poderá ser ignorado.

## <a name="severity"></a>Severidade

Para descrever a gravidade de uma violação da sua regra de nomenclatura, especifique uma propriedade no seguinte formato:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

A tabela a seguir mostra os valores de gravidade permitidos e o que eles significam:

Severidade | Efeito
------------ | -------------
nenhum | A regra foi completamente suprimida.
refatoração ou silencioso | Quando este estilo não estiver sendo seguido, não mostre nada para o usuário; no entanto, o código gerado automaticamente seguirá esse estilo.
sugestão | Quando esse estilo não estiver sendo seguido, mostre-o para o usuário como uma sugestão, como pontos subjacentes nos dois primeiros caracteres. Isso não terá nenhum efeito em tempo de compilação.
warning | Quando esse estilo não estiver sendo seguido, mostre um aviso do compilador na **Lista de Erros**.
erro | Quando esse estilo não estiver sendo seguido, mostre um erro do compilador na **Lista de Erros**.

> [!NOTE]
> Não é necessário criar seu projeto para ver as violações de regras de nomenclatura. Elas são exibidas à medida que o código é editado, na **Lista de Erros** ou como uma sugestão.

## <a name="rule-order"></a>Ordem das regras

::: moniker range="vs-2017"

As convenções de nomenclatura devem ser ordenadas da mais específica para a menos específica no arquivo EditorConfig. A primeira regra encontrada que pode ser aplicada é a única regra que é aplicada. No entanto, se houver várias *propriedades* de regras com o mesmo nome, a propriedade mais recente encontrada com esse nome terá precedência. Confira mais informações em [Precedência e hierarquia de arquivos](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

A partir do Visual Studio 2019 versão 16.2, não importa a ordem na qual as regras de nomenclatura são definidas em um arquivo EditorConfig. Em vez disso, o Visual Studio ordena as regras de nomenclatura automaticamente de acordo com a definição das próprias regras. A [extensão de serviço de linguagem EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) pode analisar um arquivo EditorConfig e casos de relatório em que a ordenação de regra no arquivo é diferente do que o compilador usará em tempo de execução.

Se você estiver usando uma versão anterior do Visual Studio, as convenções de nomenclatura deverão ser ordenadas da mais específica para a menos específica no arquivo EditorConfig. A primeira regra encontrada que pode ser aplicada é a única regra que é aplicada. No entanto, se houver várias *propriedades* de regras com o mesmo nome, a propriedade mais recente encontrada com esse nome terá precedência. Confira mais informações em [Precedência e hierarquia de arquivos](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Estilos de nomenclatura padrão

Se você não especificar todas as regras de nomenclatura personalizadas, o Visual Studio usará os seguintes estilos padrão:

- Para classes, estruturas, enumerações, propriedades e eventos com acessibilidade `public`, `private`, `internal`, `protected` ou `protected_internal`, o estilo de nomenclatura padrão é Pascal case.

- Para interfaces com acessibilidade `public`, `private`, `internal`, `protected` ou `protected_internal`, o estilo de nomenclatura padrão é Pascal case com o prefixo necessário **I**.

## <a name="example"></a>Exemplo

O arquivo *.editorconfig* a seguir contém uma convenção de nomenclatura que especifica que propriedades públicas, métodos, campos, eventos e delegados devem sempre ser escritos com maiúsculas. Observe que esta convenção de nomenclatura especifica vários tipos de símbolo aos quais aplicar a regra, usando uma vírgula para separar os valores.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

A captura de tela a seguir mostra o efeito desta convenção de nomenclatura no editor. Duas variáveis públicas foram nomeadas sem a primeira letra ser maiúscula. Uma é um `const` e a outra é `readonly`. Como a regra de nomenclatura aplica-se apenas aos símbolos `readonly`, apenas a variável `readonly` mostra uma sugestão de regra de nomenclatura.

![Sugestão de regra de nomenclatura](media/editorconfig-naming-rule-suggestion.png)

Agora vamos alterar a gravidade da violação para `warning`:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Se você fechar e reabrir o arquivo de código, em vez de ver a sugestão sob a violação de nome, verá um rabisco verde e um aviso na Lista de Erros:

![Aviso de regra de nomenclatura](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Consulte também

- [Convenções de linguagem](editorconfig-language-conventions.md)
- [Convenções de formatação](editorconfig-formatting-conventions.md)
- [Convenções de nomenclatura de Roslyn](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Criar opções do editor portátil e personalizado](../ide/create-portable-custom-editor-options.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](editorconfig-code-style-settings-reference.md)
