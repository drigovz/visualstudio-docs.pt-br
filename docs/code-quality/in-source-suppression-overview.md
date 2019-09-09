---
title: Suprimir avisos de análise de código
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 60fcb13c978d614d40964bd8d6da21e8cf41f00f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551080"
---
# <a name="suppress-code-analysis-warnings"></a>Suprimir avisos de análise de código

Geralmente, é útil indicar que um aviso não é aplicável. Isso indica aos membros da equipe que o código foi revisado e que o aviso pode ser suprimido. A supressão na origem (ISS) usa o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo para suprimir um aviso. O atributo pode ser colocado próximo ao segmento de código que gerou o aviso. Você pode adicionar o <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo ao arquivo de origem digitando-o ou pode usar o menu de atalho em um aviso no **lista de erros** para adicioná-lo automaticamente.

O <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo é um atributo condicional, que é incluído nos metadados de Il do seu assembly de código gerenciado, somente se o símbolo de compilação CODE_ANALYSIS for definido no momento da compilação.

Na C++/CLI, use a mensagem da\_AC\_de macros\_suprimida ou a SUPPRESS_MESSAGE global\_de CA no arquivo de cabeçalho para adicionar o atributo.

> [!NOTE]
> Você não deve usar supressões na origem em builds de versão, para evitar o envio acidental dos metadados de supressão na origem. Além disso, devido ao custo de processamento da supressão na origem, o desempenho do seu aplicativo pode ser degradado.

> [!NOTE]
> Se você migrar um projeto para o Visual Studio 2017 ou o Visual Studio 2019, você poderá, de repente, enfrentar um grande número de avisos de análise de código. Se você não estiver pronto para corrigir os avisos, poderá suprimir todos eles escolhendo **analisar** > **executar análise de código e suprimir problemas ativos**.
>
> ![Executar análise de código e suprimir problemas no Visual Studio](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>Atributo SuppressMessage

Quando você escolhe **suprimir** no menu de contexto ou clique com o botão direito do mouse em umaviso de análise <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> de código na lista de erros, um atributo é adicionado em seu código ou ao arquivo de supressão global do projeto.

O <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo tem o seguinte formato:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

As propriedades do atributo incluem:

- **Categoria** – a categoria na qual a regra é definida. Para obter mais informações sobre categorias de regra de análise de código, consulte [avisos de código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** -o identificador da regra. O suporte inclui um nome curto e longo para o identificador de regra. O nome curto é CAXXXX; o nome longo é CAXXXX: FriendlyTypeName.

- **Justificação** – o texto que é usado para documentar o motivo da supressão da mensagem.

- **MessageId** -identificador exclusivo de um problema para cada mensagem.

- **Escopo** -o destino no qual o aviso está sendo suprimido. Se o destino não for especificado, ele será definido como o destino do atributo. Os [escopos](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) com suporte incluem o seguinte:

  - `module`

  - `resource`

  - `type`

  - `member`

  - `namespace`-Esse escopo suprime avisos no próprio namespace. Ele não suprimi os avisos em relação aos tipos no namespace.

  - `namespaceanddescendants`-(Novo para o Visual Studio 2019) esse escopo suprime avisos em um namespace e todos os seus símbolos descendentes. O `namespaceanddescendants` valor é ignorado pela análise herdada.

- **Target** -um identificador que é usado para especificar o destino no qual o aviso está sendo suprimido. Ele deve conter um nome de item totalmente qualificado.

## <a name="suppressmessage-usage"></a>Uso de SuppressMessage

Os avisos de análise de código são suprimidos no nível ao <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> qual o atributo é aplicado. Por exemplo, o atributo pode ser aplicado no nível de assembly, módulo, tipo, membro ou parâmetro. A finalidade disso é acoplar rigidamente as informações de supressão ao código em que ocorre a violação.

A forma geral de supressão inclui a categoria de regra e um identificador de regra, que contém uma representação opcional legível do nome da regra. Por exemplo:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Se houver motivos estritos de desempenho para minimizar metadados de supressão na origem, o nome da regra poderá ser omitido. A categoria de regra e sua ID de regra juntos constituem um identificador de regra suficientemente exclusivo. Por exemplo:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Para fins de manutenção, omitir o nome da regra não é recomendado.

## <a name="suppress-selective-violations-within-a-method-body"></a>Suprimir violações seletivas dentro de um corpo de método

Atributos de supressão podem ser aplicados a um método, mas não podem ser inseridos dentro de um corpo de método. Isso significa que todas as violações de uma regra específica serão suprimidas se você adicionar <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> o atributo ao método.

Em alguns casos, talvez você queira suprimir uma instância específica da violação, por exemplo, para que o código futuro não seja automaticamente isento da regra de análise de código. Determinadas regras de análise de `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> código permitem que você faça isso usando a propriedade do atributo. Em geral, as regras herdadas para violações em um determinado símbolo (uma variável local ou parâmetro) `MessageId` respeitam a propriedade. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) é um exemplo dessa regra. No entanto, as regras herdadas para violações no código executável (não símbolo) não `MessageId` respeitam a propriedade. Além disso, os analisadores de .net Compiler Platform ("Roslyn") não `MessageId` respeitam a propriedade.

Para suprimir uma violação de símbolo específica de uma regra, especifique o nome do `MessageId` símbolo para a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Propriedade do atributo. O exemplo a seguir mostra o código com duas violações de [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;uma `name` para a variável e outra `age` para a variável. Somente a violação do `age` símbolo é suprimida.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Código gerado

Compiladores de código gerenciado e algumas ferramentas de terceiros geram código para facilitar o desenvolvimento rápido de código. O código gerado pelo compilador que aparece em arquivos de origem geralmente é marcado `GeneratedCodeAttribute` com o atributo.

Você pode escolher se deseja suprimir avisos de análise de código e erros de código gerado. Para obter informações sobre como suprimir esses avisos e erros, [consulte Como: Suprimir avisos de código](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)gerado.

> [!NOTE]
> A análise de código `GeneratedCodeAttribute` ignora quando é aplicada a um assembly inteiro ou a um único parâmetro.

## <a name="global-level-suppressions"></a>Supressões de nível global

A ferramenta de análise de código gerenciado `SuppressMessage` examina os atributos que são aplicados no nível do assembly, módulo, tipo, membro ou parâmetro. Ele também dispara violações em relação a recursos e namespaces. Essas violações devem ser aplicadas no nível global e têm escopo e destino. Por exemplo, a seguinte mensagem suprime uma violação de namespace:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando você suprimi um aviso com `namespace` escopo, ele suprime o aviso em relação ao próprio namespace. Ele não elimina o aviso em relação aos tipos no namespace.

Qualquer supressão pode ser expressa especificando um escopo explícito. Essas supressões devem residir no nível global. Não é possível especificar a supressão de nível de membro decorando um tipo.

As supressões de nível global são a única maneira de suprimir mensagens que se referem ao código gerado pelo compilador que não é mapeado para a fonte de usuário fornecida explicitamente. Por exemplo, o código a seguir suprime uma violação em relação a um Construtor emitido pelo compilador:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`sempre contém o nome do item totalmente qualificado.

## <a name="global-suppression-file"></a>Arquivo de supressão global

O arquivo de supressão global mantém supressões que são supressões de nível global ou supressões que não especificam um destino. Por exemplo, as supressões para violações no nível do assembly são armazenadas nesse arquivo. Além disso, algumas supressões ASP.NET são armazenadas nesse arquivo porque as configurações no nível do projeto não estão disponíveis para o código por trás de um formulário. Um arquivo de supressão global é criado e adicionado ao projeto na primeira vez que você seleciona a opção **no arquivo de supressão do projeto** do comando **suprimir** na janela **lista de erros** .

## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Usar analisadores de código](../code-quality/use-roslyn-analyzers.md)
