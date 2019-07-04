---
title: Convenções de linguagem .NET para EditorConfig
ms.date: 06/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2dcd0af308da3f16af461dd4b61aae3e31af0236
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67262799"
---
# <a name="language-conventions"></a>Convenções de linguagem

As convenções de linguagem para o EditorConfig no Visual Studio se enquadram em duas categorias:

- [Configurações de estilo de código do .NET](#net-code-style-settings)

- [Configurações de estilo de código de C#](#c-code-style-settings)

> [!TIP]
> Para ver os exemplos de código na sua linguagem de programação preferida, escolha-a usando o seletor de idioma no canto superior direito da janela do navegador.

## <a name="rule-format"></a>Formatação de regra

As regras para convenções de linguagem têm o seguinte formato geral:

`option_name = value:severity`

Para cada convenção de linguagem, você pode especificar um valor que define se ou quando preferir o estilo. Muitas regras aceitam um valor de `true` (preferir esse estilo) ou `false` (não preferir esse estilo); outros aceitam valores como `when_on_single_line` ou `never`. A segunda parte da regra especifica a **severidade**.

### <a name="severity"></a>Severidade

Uma severidade de convenção de linguagem especifica o nível no qual impor esse estilo. A tabela a seguir lista os valores possíveis de gravidade e seus efeitos:

Severidade | Efeito
:------- | ------
`none` | Não mostra nada para o usuário quando esta regra é violada. No entanto, os recursos de geração de código geram código neste estilo. As regras com a severidade `none` nunca são exibidas no menu **Ações Rápidas e Refatorações**. Na maioria dos casos, isso é considerado "desabilitado" ou "ignorado".
`silent` (também `refactoring` no Visual Studio 2017 versão 15.8 e posterior) | Não mostra nada para o usuário quando esta regra é violada. No entanto, os recursos de geração de código geram código neste estilo. As regras com severidade `silent` participam da limpeza e também aparecem no menu **Ações Rápidas e Refatorações**.
`suggestion` | Quando esta regra de estilo for violada, deverá ser mostrada ao usuário como uma sugestão. As sugestões são exibidas como três pontos cinza sob os dois primeiros caracteres.
`warning` | Quando esta regra de estilo for violada, deverá ser exibido um aviso do compilador.
`error` | Quando esta regra de estilo for violada, deverá ser exibido um erro do compilador.

## <a name="net-code-style-settings"></a>Configurações de estilo de código do .NET

As regras de estilo nesta seção são aplicáveis tanto para C# quanto para Visual Basic.

- [Qualificadores "This." e "Me."](#this-and-me)
   - dotnet\_style\_qualification\_for_field
   - dotnet\_style\_qualification\_for_property
   - dotnet\_style\_qualification\_for_method
   - dotnet\_style\_qualification\_for_event
- [Palavras-chave de linguagem em vez de nomes de tipos de estrutura para referências de tipo](#language-keywords)
   - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
   - dotnet\_style\_predefined\_type\_for\_member_access
- [Preferências do modificador](#normalize-modifiers)
   - dotnet\_style\_require\_accessibility_modifiers
   - csharp\_preferred\_modifier_order
   - visual\_basic\_preferred\_modifier_order
   - dotnet\_style\_readonly\_field
- [Preferências de parênteses](#parentheses-preferences)
   - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
   - dotnet\_style\_parentheses\_in\_other\_binary\_operators
   - dotnet\_style\_parentheses\_in\_other\_operators
   - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [Preferências de nível de expressão](#expression-level-preferences)
   - dotnet\_style\_object_initializer
   - dotnet\_style\_collection_initializer
   - dotnet\_style\_explicit\_tuple_names
   - dotnet\_style\_prefer\_inferred\_tuple_names
   - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
   - dotnet\_style\_prefer\_auto\_properties
   - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
   - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
   - dotnet\_style\_prefer\_conditional\_expression\_over\_return
- [Preferências da verificação de "null"](#null-checking-preferences)
   - dotnet\_style\_coalesce_expression
   - dotnet\_style\_null_propagation

### <a name="this-and-me"></a>Qualificadores "Este." e "Eu.

Essa regra de estilo pode ser aplicada a campos, propriedades, métodos ou eventos. Um valor **true** significa a preferência pelo símbolo de código ser precedido de `this.` em C# ou `Me.` no Visual Basic. Um valor **false** significa a preferência pelo elemento de código _não_ ser precedido de `this.` ou `Me.`.

Essas regras podem aparecer em um arquivo *.editorconfig*, assim como mostrado a seguir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnetstylequalificationforfield"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Nome da regra** | dotnet_style_qualification_for_field |
| **ID da regra** | IDE0003 e IDE0009 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir que os campos sejam precedidos por `this.` em C# ou `Me.` no Visual Basic<br /><br />`false` – preferir que os campos _não_ sejam precedidos por `this.` ou `Me.` |
| **Padrão do Visual Studio** | `false:silent` |

Exemplos de código:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

#### <a name="dotnetstylequalificationforproperty"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Nome da regra** | dotnet_style_qualification_for_property |
| **ID da regra** | IDE0003 e IDE0009 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir que as propriedades sejam precedidas com `this.` em C# ou `Me.` no Visual Basic<br /><br />`false` – preferir que as propriedades _não_ sejam precedidas com `this.` ou `Me.` |
| **Padrão do Visual Studio** | `false:silent` |

Exemplos de código:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

#### <a name="dotnetstylequalificationformethod"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Nome da regra** | dotnet_style_qualification_for_method |
| **ID da regra** | IDE0003 e IDE0009 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir que os métodos sejam precedidos por `this.` em C# ou `Me.` no Visual Basic.<br /><br />`false` – preferir que os métodos _não_ sejam precedidos por `this.` ou `Me.`. |
| **Padrão do Visual Studio** | `false:silent` |

Exemplos de código:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

#### <a name="dotnetstylequalificationforevent"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Nome da regra** | dotnet_style_qualification_for_event |
| **ID da regra** | IDE0003 e IDE0009 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir que os eventos sejam precedidos por `this.` em C# ou `Me.` no Visual Basic.<br /><br />`false` – preferir que os eventos _não_ sejam precedidos por `this.` ou `Me.`. |
| **Padrão do Visual Studio** | `false:silent` |

Exemplos de código:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

### <a name="language-keywords"></a>Palavras-chave de linguagem em vez de nomes de tipos de estrutura para referências de tipo

Essa regra de estilo pode ser aplicada a variáveis locais, parâmetros de método e membros de classe ou como uma regra separada para expressões de acesso a membro de tipo. Um valor **true** significa preferência pela palavra-chave de linguagem (por exemplo, `int` ou `Integer`) em vez do nome do tipo (por exemplo, `Int32`) para tipos que têm uma palavra-chave para representá-los. Um valor **false** significa preferência pelo nome do tipo em vez da palavra-chave de linguagem.

Essas regras podem aparecer em um arquivo *.editorconfig*, assim como mostrado a seguir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnetstylepredefinedtypeforlocalsparametersmembers"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Nome da regra** | dotnet_style_predefined_type_for_locals_parameters_members |
| **ID da regra** | IDE0012 e IDE0014 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir a palavra-chave de linguagem para variáveis locais, parâmetros de método e membros de classe, em vez do nome de tipo, para tipos que têm uma palavra-chave para representá-los<br /><br />`false` – preferir o nome do tipo para variáveis locais, parâmetros de método e membros de classe, em vez da palavra-chave de linguagem |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

#### <a name="dotnetstylepredefinedtypeformemberaccess"></a>dotnet\_style\_predefined\_type\_for\_member_access

|||
|-|-|
| **Nome da regra** | dotnet_style_predefined_type_for_member_access |
| **ID da regra** | IDE0013 e IDE0015 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir a palavra-chave de linguagem para expressões de acesso a membro, em vez do nome de tipo, para tipos que têm uma palavra-chave para representá-los<br /><br />`false` – preferir o nome do tipo para expressões de acesso a membro, em vez da palavra-chave de linguagem |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

### <a name="normalize-modifiers"></a>Preferências do modificador

As regras de estilo desta seção dizem respeito às preferências do modificador, incluindo a exigência de modificadores de acessibilidade, a especificação da ordem de classificação de modificador desejada e a exigência do modificador somente leitura.

Essas regras podem aparecer em um arquivo *.editorconfig*, assim como mostrado a seguir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="dotnetstylerequireaccessibilitymodifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Nome da regra** | dotnet_style_require_accessibility_modifiers |
| **ID da regra** | IDE0040 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `always` – preferir que modificadores de acessibilidade sejam especificados.<br /><br />`for_non_interface_members` – preferir que modificadores de acessibilidade sejam declarados, exceto os membros de interface pública. (Isso é o mesmo que **always** e foi adicionado para durabilidade, caso o C# adicione métodos de interface padrão.)<br /><br />`never` – não preferir que modificadores de acessibilidade sejam especificados.<br /><br />`omit_if_default` – preferir que modificadores de acessibilidade sejam especificados, exceto se forem o modificador padrão. |
| **Padrão do Visual Studio** | `for_non_interface_members:silent` |
| **Versão introduzida** | Visual Studio 2017 versão 15.5 |

Exemplos de código:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

#### <a name="csharppreferredmodifierorder"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Nome da regra** | csharp_preferred_modifier_order |
| **ID da regra** | IDE0036 |
| **Linguagens aplicáveis** | C# |
| **Valores** | Um ou mais modificadores de C#, como `public`, `private`, e `protected` |
| **Padrão do Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Versão introduzida** | Visual Studio 2017 versão 15.5 |

- Quando esta regra for definida como uma lista de modificadores, prefira a ordenação especificada.
- Quando esta regra for omitida do arquivo, não prefira uma ordem de modificador.

Exemplos de código:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visualbasicpreferredmodifierorder"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Nome da regra** | visual_basic_preferred_modifier_order |
| **ID da regra** | IDE0036 |
| **Linguagens aplicáveis** | Visual Basic |
| **Valores** | Um ou mais modificadores de Visual Basic, como `Partial`, `Private`, e `Public` |
| **Padrão do Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Versão introduzida** | Visual Studio 2017 versão 15.5 |

- Quando esta regra for definida como uma lista de modificadores, prefira a ordenação especificada.
- Quando esta regra for omitida do arquivo, não prefira uma ordem de modificador.

Exemplos de código:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="dotnetstylereadonlyfield"></a>dotnet_style_readonly_field

|||
|-|-|
| **Nome da regra** | dotnet_style_readonly_field |
| **ID da regra** | IDE0044 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir que os campos sejam marcados com `readonly` (C#) ou `ReadOnly` (Visual Basic), caso sejam somente atribuídos de maneira embutida ou dentro de um construtor<br /><br />`false` – não especifique nenhuma preferência sobre se os campos devem ser marcados com `readonly` (C#) ou `ReadOnly` (Visual Basic) |
| **Padrão do Visual Studio** | `true:suggestion` |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |

Exemplos de código:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

### <a name="parentheses-preferences"></a>Preferências de parênteses

As regras de estilo nesta seção referem-se às preferências de parênteses, incluindo o uso de parênteses para operadores aritméticos, relacionais e outros operadores binários.

Essas regras podem aparecer em um arquivo *.editorconfig*, assim como mostrado a seguir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnetstyleparenthesesinarithmeticbinaryoperators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|||
|-|-|
| **Nome da regra** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **ID da regra** | IDE0047 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `always_for_clarity` – preferir parênteses para esclarecer a precedência do operador aritmético (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`)<br /><br />`never_if_unnecessary` – preferir não usar parênteses quando a precedência do operador aritmético (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) for óbvia |
| **Padrão do Visual Studio** | `always_for_clarity:silent` |
| **Versão introduzida** | Visual Studio 2017 versão 15.8 |

Exemplos de código:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnetstyleparenthesesinrelationalbinaryoperators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|||
|-|-|
| **Nome da regra** | dotnet_style_parentheses_in_relational_binary_operators |
| **ID da regra** | IDE0047 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `always_for_clarity` - preferir parênteses para esclarecer a precedência do operador relacional (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`)<br /><br />`never_if_unnecessary` – preferir não usar parênteses quando a precedência do operador relacional (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) for óbvia |
| **Padrão do Visual Studio** | `always_for_clarity:silent` |
| **Versão introduzida** | Visual Studio 2017 versão 15.8 |

Exemplos de código:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnetstyleparenthesesinotherbinaryoperators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|||
|-|-|
| **Nome da regra** | dotnet_style_parentheses_in_other_binary_operators |
| **ID da regra** | IDE0047 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `always_for_clarity` – preferir parênteses para esclarecer a precedência do outro operador binário (`&&`, `||`, `??`)<br /><br />`never_if_unnecessary` – preferir não usar parênteses quando a precedência do outro operador binário (`&&`, `||`, `??`) for óbvia |
| **Padrão do Visual Studio** | `always_for_clarity:silent` |
| **Versão introduzida** | Visual Studio 2017 versão 15.8 |

Exemplos de código:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnetstyleparenthesesinotheroperators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Nome da regra** | dotnet_style_parentheses_in_other_operators |
| **ID da regra** | IDE0047 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `always_for_clarity` – preferir parênteses para esclarecer a precedência do operador<br /><br />`never_if_unnecessary` – preferir não usar parênteses quando a precedência do operador for óbvia |
| **Padrão do Visual Studio** | `never_if_unnecessary:silent` |
| **Versão introduzida** | Visual Studio 2017 versão 15.8 |

Exemplos de código:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>Preferências de nível de expressão

As regras de estilo nesta seção referem-se às preferências no nível da expressão, incluindo o uso de inicializadores de objeto, inicializadores de coleção, nomes de tupla explícitos ou inferidos e tipos anônimos inferidos.

Essas regras podem aparecer em um arquivo *.editorconfig*, assim como mostrado a seguir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="dotnetstyleobjectinitializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Nome da regra** | dotnet_style_object_initializer |
| **ID da regra** | IDE0017 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir objetos que sejam inicializados usando inicializadores de objeto quando possível<br /><br />`false` – preferir objetos que *não* sejam inicializados usando inicializadores de objeto |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

#### <a name="dotnetstylecollectioninitializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Nome da regra** | dotnet_style_collection_initializer |
| **ID da regra** | IDE0028 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – prefira coleções que sejam inicializadas usando inicializadores de coleção quando possível<br /><br />`false` – preferir objetos que *não* sejam inicializados usando inicializadores de coleção |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

#### <a name="dotnetstyleexplicittuplenames"></a>dotnet\_style\_explicit\_tuple_names

|||
|-|-|
| **Nome da regra** | dotnet_style_explicit_tuple_names |
| **ID da regra** | IDE0033 |
| **Linguagens aplicáveis** | C# 7.0+ e Visual Basic 15+ |
| **Valores** | `true` – preferir nomes de tupla a propriedades ItemX<br /><br />`false` – preferir propriedades ItemX a nomes de tupla |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

#### <a name="dotnetstylepreferinferredtuplenames"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|||
|-|-|
| **Nome da regra** | dotnet_style_prefer_inferred_tuple_names |
| **ID da regra** | IDE0037 |
| **Linguagens aplicáveis** | C# 7.1+ e Visual Basic 15+ |
| **Valores** | `true` – preferir nomes de elementos de tupla inferidos<br /><br />`false` – preferir nomes de elemento de tupla explícita |
| **Padrão do Visual Studio** | `true:suggestion` |
| **Versão introduzida** | Visual Studio 2017 versão 15.6 |

Exemplos de código:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnetstylepreferinferredanonymoustypemembernames"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|||
|-|-|
| **Nome da regra** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **ID da regra** | IDE0037 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir nomes de membro do tipo anônimo inferidos<br /><br />`false` – preferir nomes de membro do tipo anônimo explícitos |
| **Padrão do Visual Studio** | `true:suggestion` |
| **Versão introduzida** | Visual Studio 2017 versão 15.6 |

Exemplos de código:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnetstylepreferautoproperties"></a>dotnet\_style\_prefer\_auto\_properties

|||
|-|-|
| **Nome da regra** | dotnet_style_prefer_auto_properties |
| **ID da regra** | IDE0032 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir propriedades automáticas em vez de propriedades com campos de suporte particular<br /><br />`false` – preferir propriedades com campos de suporte particular em vez de propriedades automáticas |
| **Padrão do Visual Studio** | `true:suggestion` |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |

Exemplos de código:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnetstylepreferisnullcheckoverreferenceequalitymethod"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Nome da regra** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID da regra** | IDE0041 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir usar uma verificação nula com correspondência de padrões em vez de `object.ReferenceEquals`<br /><br />`false` – preferir usar `object.ReferenceEquals` em vez de uma verificação nula com correspondência de padrões |
| **Padrão do Visual Studio** | `true:suggestion` |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |

Exemplos de código:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnetstylepreferconditionalexpressionoverassignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Nome da regra** | dotnet_style_prefer_conditional_expression_over_assignment |
| **ID da regra** | IDE0045 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir atribuições com uma condicional ternária em vez de uma instrução if-else<br /><br />`false` – preferir atribuições com uma instrução if-else em vez de uma condicional ternária |
| **Padrão do Visual Studio** | `true:suggestion` |
| **Versão introduzida** | Visual Studio 2017 versão 15.8 |

Exemplos de código:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnetstylepreferconditionalexpressionoverreturn"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Nome da regra** | dotnet_style_prefer_conditional_expression_over_return |
| **ID da regra** | IDE0046 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir que as instruções de retorno usem uma condicional ternária em vez de uma instrução if-else<br /><br />`false` – preferir que as instruções de retorno usem uma instrução if-else em vez de uma condicional ternária |
| **Padrão do Visual Studio** | `true:suggestion` |
| **Versão introduzida** | Visual Studio 2017 versão 15.8 |

Exemplos de código:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

### <a name="null-checking-preferences"></a>Preferências de verificação nula

As regras de estilo nesta seção referem-se às preferências de verificação de nulo.

Essas regras podem aparecer em um arquivo *.editorconfig*, assim como mostrado a seguir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

#### <a name="dotnetstylecoalesceexpression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Nome da regra** | dotnet_style_coalesce_expression |
| **ID da regra** | IDE0029 |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Valores** | `true` – preferir expressões de coalescência nula a verificação do operador ternário<br /><br />`false` – preferir verificação do operador ternário a expressões de coalescência nula |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

#### <a name="dotnetstylenullpropagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Nome da regra** | dotnet_style_null_propagation |
| **ID da regra** | IDE0031 |
| **Linguagens aplicáveis** | C# 6.0+ e Visual Basic 14+ |
| **Valores** | `true` – preferir usar o operador condicional nulo quando possível<br /><br />`false` – preferir usar a verificação nula ternária quando possível |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

## <a name="c-code-style-settings"></a>Configurações de estilo de código de C#

As regras de estilo nesta seção são aplicáveis somente á linguagem C#.

- [Tipos implícitos e explícitos](#implicit-and-explicit-types)
   - csharp\_style\_var\_for\_built\_in_types
   - csharp\_style\_var\_when\_type\_is_apparent
   - csharp\_style\_var_elsewhere
- [Membros de expressão incorporada](#expression-bodied-members)
   - csharp\_style\_expression\_bodied_methods
   - csharp\_style\_expression\_bodied_constructors
   - csharp\_style\_expression\_bodied_operators
   - csharp\_style\_expression\_bodied_properties
   - csharp\_style\_expression\_bodied_indexers
   - csharp\_style\_expression\_bodied_accessors
- [Correspondência de padrões](#pattern-matching)
   - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
   - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [Declarações de variável embutida](#inlined-variable-declarations)
   - csharp\_style\_inlined\_variable_declaration
- [Preferências de nível de expressão](#expression-level-preferences)
   - csharp\_prefer\_simple\_default_expression
   - csharp\_style\_deconstructed\_variable_declaration
   - csharp\_style\_pattern\_local\_over\_anonymous_function
- [Preferências da verificação de "null"](#null-checking-preferences)
   - csharp\_style\_throw_expression
    - csharp\_style\_conditional\_delegate_call
- [Preferências de bloco de código](#code-block-preferences)
   - csharp\_prefer_braces

### <a name="implicit-and-explicit-types"></a>Tipos implícitos e explícitos

As regras de estilo nesta seção referem-se ao uso da palavra-chave [var](/dotnet/csharp/language-reference/keywords/var) em vez de um tipo explícito em uma declaração de variável. Essa regra pode ser aplicada separadamente a tipos internos, quando o tipo é aparente e em qualquer outro local.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharpstylevarforbuiltintypes"></a>csharp\_style\_var\_for\_built\_in_types

|||
|-|-|
| **Nome da regra** | csharp_style_var_for_built_in_types |
| **ID da regra** | IDE0007 e IDE0008 |
| **Linguagens aplicáveis** | C#  |
| **Valores** | `true` – preferir usar `var` para declarar variáveis com tipos de sistema internos, como `int`<br /><br />`false` – preferir o tipo explícito em vez de `var` para declarar variáveis com tipos de sistema internos, como `int` |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharpstylevarwhentypeisapparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Nome da regra** | csharp_style_var_when_type_is_apparent |
| **ID da regra** | IDE0007 e IDE0008 |
| **Linguagens aplicáveis** | C#  |
| **Valores** | `true` – preferir `var` quando o tipo já tiver sido mencionado no lado direito de uma expressão de declaração<br /><br />`false` – preferir o tipo explícito em vez de `var` quando o tipo já tiver sido mencionado no lado direito de uma expressão de declaração |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharpstylevarelsewhere"></a>csharp\_style\_var_elsewhere

|||
|-|-|
| **Nome da regra** | csharp_style_var_elsewhere |
| **ID da regra** | IDE0007 e IDE0008 |
| **Linguagens aplicáveis** | C#  |
| **Valores** | `true` – preferir `var` em vez de tipo explícito em todos os casos, a menos que a regra seja substituída por outra regra de estilo de código<br /><br />`false` – preferir o tipo explícito em vez de `var` em todos os casos, a menos que a regra seja substituída por outra regra de estilo de código |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Membros aptos para expressão

As regras de estilo nesta seção envolvem o uso de [membros aptos para expressão](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) quando a lógica consiste em uma única expressão. Essa regra pode ser aplicada a métodos, construtores, operadores, propriedades, indexadores e acessadores.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="csharpstyleexpressionbodiedmethods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Nome da regra** | csharp_style_expression_bodied_methods |
| **ID da regra** | IDE0022 |
| **Linguagens aplicáveis** | C# 6.0+  |
| **Valores** | `true` – preferir membros aptos para expressão para métodos<br /><br />`when_on_single_line` – preferir membros aptos para expressão para métodos quando eles forem uma única linha<br /><br />`false` – preferir corpos de bloco para métodos |
| **Padrão do Visual Studio** | `false:silent` |

Exemplos de código:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharpstyleexpressionbodiedconstructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Nome da regra** | csharp_style_expression_bodied_constructors |
| **ID da regra** | IDE0021 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir membros aptos para expressão para construtores<br /><br />`when_on_single_line` – preferir membros aptos para expressão para construtores quando eles forem uma única linha<br /><br />`false` – preferir corpos de bloco para construtores |
| **Padrão do Visual Studio** | `false:silent` |

Exemplos de código:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharpstyleexpressionbodiedoperators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Nome da regra** | csharp_style_expression_bodied_operators |
| **ID da regra** | IDE0023 e IDE0024 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir membros aptos para expressão para operadores<br /><br />`when_on_single_line` – preferir membros aptos para expressão para operadores quando forem uma única linha<br /><br />`false` – preferir corpos de blocos para operadores |
| **Padrão do Visual Studio** | `false:silent` |

Exemplos de código:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharpstyleexpressionbodiedproperties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Nome da regra** | csharp_style_expression_bodied_properties |
| **ID da regra** | IDE0025 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir membros aptos para expressão para propriedades<br /><br />`when_on_single_line` – preferir membros aptos para expressão para propriedades quando elas forem uma única linha<br /><br />`false` – preferir blocos do corpo para propriedades |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharpstyleexpressionbodiedindexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Nome da regra** | csharp_style_expression_bodied_indexers |
| **ID da regra** | IDE0026 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir membros aptos para expressão para indexadores<br /><br />`when_on_single_line` – preferir membros aptos para expressão para indexadores quando eles forem uma única linha<br /><br />`false` – preferir blocos do corpo para indexadores |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharpstyleexpressionbodiedaccessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Nome da regra** | csharp_style_expression_bodied_accessors |
| **ID da regra** | IDE0027 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir membros aptos para expressão para acessadores<br /><br />`when_on_single_line` – preferir membros aptos para expressão para acessadores quando eles forem uma única linha<br /><br />`false` – preferir blocos do corpo para acessadores |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

### <a name="pattern-matching"></a>Correspondência de padrões

As regras de estilo nesta seção envolvem o uso de [correspondência de padrões](/dotnet/csharp/pattern-matching) em C#.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharpstylepatternmatchingoveriswithcastcheck"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|||
|-|-|
| **Nome da regra** | csharp_style_pattern_matching_over_is_with_cast_check |
| **ID da regra** | IDE0020 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – prefira a correspondência de padrões a expressões `is` com conversões de tipo<br /><br />`false` – prefira expressões `is` com conversões de tipo a correspondência de padrões |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharpstylepatternmatchingoveraswithnullcheck"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|||
|-|-|
| **Nome da regra** | csharp_style_pattern_matching_over_as_with_null_check |
| **ID da regra** | IDE0019 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – prefira correspondência de padrões a expressões `as` com verificações nulas para determinar se algo é de um tipo específico<br /><br />`false` – prefira expressões `as` com verificações de null a correspondência de padrões para determinar se algo é de um tipo específico |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Declarações de variável embutida

Essa regra de estilo é relacionada a se as variáveis `out` são declaradas embutidas ou não. Após o C#7, você pode [declarar uma variável de saída na lista de argumentos de uma chamada de método](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument) em vez de declará-la em uma declaração de variável separada.

#### <a name="csharpstyleinlinedvariabledeclaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Nome da regra** | csharp_style_inlined_variable_declaration |
| **ID da regra** | IDE0018 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir que as variáveis `out` sejam declaradas embutidas na lista de argumentos de uma chamada de método quando possível<br /><br />`false` – preferir `out` variáveis sejam declaradas antes da chamada de método |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="expression-level-preferences"></a>Preferências de nível de expressão

As regras de estilo nesta seção dizem respeito às preferências de nível de expressão, incluindo o uso de [expressões padrão](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), variáveis desconstruídas e funções locais em vez de funções anônimas.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="csharpprefersimpledefaultexpression"></a>csharp\_prefer\_simple\_default_expression

Essa regra de estilo refere-se ao uso do [literal `default` para expressões de valor padrão](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) quando o compilador pode inferir o tipo da expressão.

|||
|-|-|
| **Nome da regra** | csharp_prefer_simple_default_expression |
| **ID da regra** | IDE0034 |
| **Linguagens aplicáveis** | C# 7.1+  |
| **Valores** | `true` – preferir `default` a `default(T)`<br /><br />`false` – preferir `default(T)` a `default` |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

#### <a name="csharpstyledeconstructedvariabledeclaration"></a>csharp\_style\_deconstructed\_variable_declaration

|||
|-|-|
| **Nome da regra** | csharp_style_deconstructed_variable_declaration |
| **ID da regra** | IDE0042 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir declaração de variável desconstruída<br /><br />`false` – não preferir a desconstrução em declarações de variável |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

#### <a name="csharpstylepatternlocaloveranonymousfunction"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

|||
|-|-|
| **Nome da regra** | csharp_style_pattern_local_over_anonymous_function |
| **ID da regra** | IDE0039 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir as funções locais em vez de funções anônimas<br /><br />`false` – preferir as funções anônimas em vez de funções locais |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

### <a name="null-checking-preferences"></a>Preferências de verificação nula

Essas regras de estilo referem-se à sintaxe da verificação de `null`, incluindo o uso de expressões `throw` ou instruções `throw`, e se é desejável executar uma verificação nula ou usar o operador de união condicional (`?.`) ao invocar uma [expressão lambda](/dotnet/csharp/lambda-expressions).

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharpstylethrowexpression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Nome da regra** | csharp_style_throw_expression |
| **ID da regra** | IDE0016 |
| **Linguagens aplicáveis** | C# 7.0+  |
| **Valores** | `true` – preferir usar expressões `throw` a usar instruções `throw`<br /><br />`false` – preferir usar instruções `throw` a usar expressões `throw` |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharpstyleconditionaldelegatecall"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Nome da regra** | csharp_style_conditional_delegate_call |
| **ID da regra** | IDE0041 |
| **Linguagens aplicáveis** | C# 6.0+  |
| **Valores** | `true` – preferir usar o operador de união condicional (`?.`) ao invocar uma expressão lambda, em vez de realizar uma verificação nula<br /><br />`false` – preferir realizar uma verificação nula antes de invocar uma expressão lambda a usar o operador de união condicional (`?.`) |
| **Padrão do Visual Studio** | `true:suggestion` |

Exemplos de código:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Preferências de bloco de código

Essa regra de estilo diz respeito ao uso de chaves `{ }` para cercar blocos de código.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharppreferbraces"></a>csharp\_prefer\_braces

|||
|-|-|
| **Nome da regra** | csharp_prefer_braces |
| **ID da regra** | IDE0011 |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – preferir chaves, até mesmo para uma linha de código<br /><br />`false` – preferir não usar chaves se permitido |
| **Padrão do Visual Studio** | `true:silent` |

Exemplos de código:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

## <a name="see-also"></a>Consulte também

- [Convenções de formatação](editorconfig-formatting-conventions.md)
- [Convenções de nomenclatura](editorconfig-naming-conventions.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](editorconfig-code-style-settings-reference.md)