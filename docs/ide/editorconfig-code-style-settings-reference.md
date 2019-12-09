---
title: Configurações de convenção de codificação do .NET para o EditorConfig
ms.date: 06/14/2018
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 99d83157e2b6d108eb87a701aa8bc05ca2c7b1e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653712"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Configurações de convenção de codificação do .NET para o EditorConfig

Você pode definir e manter um estilo de código consistente em sua base de código com o uso de um arquivo [EditorConfig](../ide/create-portable-custom-editor-options.md). O EditorConfig inclui várias propriedades de formatação de núcleo, como `indent_style` e `indent_size`. No Visual Studio, as definições de convenções de codificação do .NET também podem ser configuradas usando um arquivo EditorConfig. É possível habilitar ou desabilitar convenções individuais de codificação do .NET e configurar o grau de imposição de cada regra por meio de um nível de gravidade.

> [!TIP]
> - Ao definir convenções de codificação em um arquivo EditorConfig, você está configurando como deseja que os [analisadores de estilo de código](../code-quality/roslyn-analyzers-overview.md) que são criados no Visual Studio analisem seu código. O arquivo EditorConfig é o arquivo de configuração para esses analisadores.
> - As preferências de estilo de código do Visual Studio também podem ser definidas na caixa de diálogo [Opções do editor de texto](code-styles-and-code-cleanup.md). No entanto, as configurações de EditorConfig têm precedência e as preferências definidas em **Opções** não são associadas a um projeto específico.

## <a name="convention-categories"></a>Categorias de convenção

Há três categorias de convenção de codificação .NET com suporte:

- [Convenções de linguagem](../ide/editorconfig-language-conventions.md)

   Regras referentes à linguagem C# ou Visual Basic. Por exemplo, você pode especificar regras sobre o uso de `var` ou tipos explícitos ao definir variáveis ou dar preferência a membros aptos para expressão.

- [Convenções de formatação](../ide/editorconfig-formatting-conventions.md)

   Regras sobre o layout e a estrutura do seu código para facilitar a leitura. Por exemplo, você pode especificar regras em relação a chaves Allman ou dar preferência a espaços em blocos de controle.

- [Convenções de nomenclatura](../ide/editorconfig-naming-conventions.md)

   Regras relacionadas a nomenclatura dos elementos de código. Por exemplo, você pode especificar que os métodos `async` devem terminar com "Async".

## <a name="example-editorconfig-file"></a>Exemplo de arquivo EditorConfig

Para ajudá-lo a começar, este é um arquivo *.editorconfig* de exemplo com as opções padrão:

```ini
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_property = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_event = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:silent
csharp_style_var_when_type_is_apparent = true:silent
csharp_style_var_elsewhere = true:silent

# Expression-bodied members
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_accessors = true:silent

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:silent
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_after_comma = true
csharp_space_after_dot = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Consulte também

- [Ações rápidas](../ide/quick-actions.md)
- [Criar opções do editor portátil e personalizado](../ide/create-portable-custom-editor-options.md)
- [Arquivo .editorconfig da plataforma do compilador do .NET](https://github.com/dotnet/roslyn/blob/master/.editorconfig)