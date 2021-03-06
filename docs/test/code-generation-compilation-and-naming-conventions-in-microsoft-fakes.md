---
title: 'Falsificações da Microsoft: gerar & código de compilação; convenções de nomenclatura'
description: Saiba mais sobre as opções e problemas na geração e compilação de código de falsificações, incluindo as convenções de nomenclatura para falsificações geradas tipos, membros e parâmetros.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ecba59e633bf6d456f16e6098f47719e052ac0de
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006359"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Geração de código, compilação e convenções de nomenclatura no Microsoft Fakes

Este artigo discute problemas e opções na compilação e geração de código do Fakes e descreve as convenções de nomenclatura para tipos, membros e parâmetros gerados pelo Fakes.

**Requirements**

- Visual Studio Enterprise
- Um projeto do .NET Framework
::: moniker range=">=vs-2019"
- O .NET Core, o .NET 5,0 e o projeto em estilo SDK oferecem suporte à visualização no Visual Studio 2019 atualização 6 e são habilitados por padrão na atualização 8. Para obter mais informações, consulte [falsificações da Microsoft para projetos do estilo SDK e do .NET Core](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

## <a name="code-generation-and-compilation"></a>Geração e compilação de código

### <a name="configure-code-generation-of-stubs"></a>Configurar a geração de código de stubs

A geração de tipos de stub é configurada em um arquivo XML que tem a extensão de arquivo *.fakes*. A estrutura do Fakes integra-se no processo de build por meio de tarefas personalizadas do MSBuild e detecta esses arquivos no momento do build. O gerador de código do Fakes compila os tipos de stub em um assembly e adiciona a referência ao projeto.

O exemplo a seguir ilustra os tipos de stub definidos em *FileSystem.dll*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Filtragem de tipo

Filtros podem ser configurados no arquivo *.fakes* para restringir os tipos que devem conter stubs. Você pode adicionar um número ilimitado de elementos Clear, Add e Remove sob o elemento StubGeneration para criar a lista de tipos selecionados.

Por exemplo, o arquivo *.fakes* a seguir gera stubs para tipos nos namespaces System e System.IO mas exclui qualquer tipo que contém "Handle" em System:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

As cadeias de caracteres de filtro usam uma gramática simples para definir como a correspondência deve ser feita:

- Filtros não diferenciam maiúsculas de minúsculas por padrão; os filtros executam uma correspondência de subcadeia de caracteres:

     `el` corresponde a "hello"

- Adicionar `!` ao final do filtro torna essa uma correspondência precisa que diferencia maiúsculas e minúsculas:

     `el!` não corresponde a "hello"

     `hello!` corresponde a "hello"

- Adicionar `*` ao final do filtro faz com que ele corresponda ao prefixo da cadeia de caracteres:

     `el*` não corresponde a "hello"

     `he*` corresponde a "hello"

- Vários filtros em uma lista separada por ponto e vírgula são combinados como uma disjunção:

     `el;wo` corresponde a "hello" e "world"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Classes concretas de stub e métodos virtuais

Por padrão, os tipos de stub são gerados para todas as classes não lacradas. É possível restringir os tipos de stub para classes abstratas por meio de arquivo de configuração *.fakes*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="internal-types"></a>Tipos internos

O gerador de código do Fakes gera tipos de shim e tipos de stub que são visíveis para o assembly do Fakes gerado. Para tornar os tipos internos de um assembly com shims visível para o Fakes e para seu assembly de teste, adicione atributos <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> no código do assembly com shims que proporciona visibilidade para o assembly do Fakes gerado e para o assembly de teste. Aqui está um exemplo:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Tipos internos em assemblies com nomes fortes**

Se o assembly com shims tiver um nome forte e você quiser acessar tipos internos do assembly:

- Ambos seu assembly de teste e o assembly do Fakes devem ter nomes fortes.

- Adicione as chaves públicas do assemblies do Fakes e do teste aos atributos **InternalsVisibleToAttribute** nos assemblies com shims. Veja como os atributos de exemplo no código de assembly com shims ficariam quando o assembly com shims tivesse nome forte:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Se o assembly com shims tivesse um nome forte, a estrutura do Fakes assinaria automaticamente fortemente o assembly do Fakes gerado. Você precisa assinar fortemente o assembly de teste. Confira [Assemblies de nome forte](/dotnet/framework/app-domains/strong-named-assemblies).

A estrutura do Fakes usa a mesma chave para assinar assemblies gerados, então você pode usar este snippet de código como um ponto de partida para adicionar o atributo **InternalsVisibleTo** do assembly do Fakes ao seu código de assembly com shims.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Você pode especificar uma chave pública diferente para o assembly de falsificações, como uma chave que você criou para o assembly corrigido, especificando o caminho completo para o arquivo *. SNK* que contém a chave alternativa como o `KeyFile` valor do atributo no `Fakes` \\ `Compilation` elemento do arquivo *. falsificações* . Por exemplo:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Em seguida, você deve usar a chave pública do arquivo *.snk* alternativo como o segundo parâmetro do atributo InternalVisibleTo para o assembly do Fakes no código de assembly com shims:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

No exemplo acima, os valores de `Alternate_public_key` e `Test_assembly_public_key` podem ser iguais.

### <a name="optimize-build-times"></a>Otimizar tempos de build

O build de assemblies do Fakes pode aumentar significativamente o tempo de build. Você pode minimizar o tempo de build, gerando os assemblies do Fakes para assemblies do .NET System e assemblies de terceiros em um projeto centralizado separado. Já que esses assemblies raramente são alterados em seu computador, é possível reutilizar os assemblies do Fakes gerados em outros projetos.

De seus projetos de teste de unidade, faça uma referência aos assemblies do Fakes compilados que são colocados em FakesAssemblies na pasta do projeto.

1. Crie uma nova biblioteca de classes com a versão de runtime do .NET que corresponde aos seus projetos de teste. Vamos chamá-lo de Fakes.Prebuild. Remova o arquivo *Class1.cs* do projeto, não necessário.

2. Adicione uma referência a todos os assemblies do System e de terceiros para os quais você precisa do Fakes.

3. Adicione um arquivo *.fakes* para cada um dos assemblies e crie.

4. Do seu projeto de teste

    - Certifique-se de que você tem uma referência para a DLL de runtime do Fakes:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Para cada assembly para o qual você criou o Fakes, adicione uma referência ao arquivo DLL correspondente na pasta *Fakes.Prebuild\FakesAssemblies* do projeto.

### <a name="avoid-assembly-name-clashing"></a>Evitar conflitos entre nomes de assembly

Em um ambiente do Team Build, todas as saídas de build são mescladas em um único diretório. Se vários projetos usarem o Fakes, poderá acontecer que assemblies do Fakes de versões diferentes substituam uns aos outros. Por exemplo, o TestProject1 fakes *mscorlib.dll* do .NET Framework 2.0 e o TestProject2 fakes *mscorlib.dll* para o .NET Framework 4 produziriam um assembly do Fakes *mscorlib.Fakes.dll*.

Para evitar esse problema, o Fakes deve criar automaticamente nomes de assembly do Fakes de versão qualificada para referências que não sejam do projeto ao adicionar os arquivos *.fakes*. Um nome de assembly do Fakes de versão qualificada incorpora um número de versão quando você cria o nome de assembly do Fakes:

Dado um assembly MyAssembly e uma versão 1.2.3.4, o nome de assembly do Fakes é MyAssembly.1.2.3.4.Fakes.

Você pode alterar ou remover essa versão editando o atributo Version do elemento de Assembly no *.fakes*:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Convenções de nomenclatura do Fakes

### <a name="shim-type-and-stub-type-naming-conventions"></a>Convenções de nomenclatura de tipo de shim e tipo de stub

**Namespaces**

- O sufixo .fakes é adicionado ao namespace.

   Por exemplo, o namespace `System.Fakes` contém os tipos de shim do namespace System.

- Global.Fakes contém o tipo de shim do namespace vazio.

  **Nomes de tipos**

- O prefixo Shim é adicionado ao nome de tipo para criar o nome de tipo do shim.

   Por exemplo, ShimExample é o tipo de shim do tipo Example.

- O prefixo Stub é adicionado ao nome de tipo para criar o nome de tipo do stub.

   Por exemplo, StubIExample é o tipo de stub do tipo IExample.

  **Argumentos de tipo e estruturas de tipo aninhado**

- Os argumentos de tipo genérico são copiados.

- A estrutura de tipo aninhado é copiada para os tipos de shim.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Convenções de nomenclatura de propriedade delegada de shim ou campo delegado de stub

**Regras básicas** para nomenclatura de campos, começando por um nome vazio:

- O nome do método é acrescentado.

- Se o nome do método for uma implementação de interface explícita, os pontos serão removidos.

- Se o método for genérico, `Of`*n* será acrescentado, em que *n* é o número de argumentos de método genérico.

  **Nomes de métodos especiais** , como getter ou setters de propriedade, são tratados conforme descrito na tabela a seguir:

|Se o método for...|Exemplo|Nome do método anexado|
|-|-|-|
|Um **Construtor**|`.ctor`|`Constructor`|
|Um **construtor** estático|`.cctor`|`StaticConstructor`|
|Um **acessador** com nome de método composto de duas partes separadas por "_" (como getters de propriedade)|*kind_name* (caso mais frequente, mas não imposto por ECMA)|*NameKind*, em que ambas as partes foram colocadas em maiusculas e trocadas|
||Getter de propriedade `Prop`|`PropGet`|
||Setter de propriedade `Prop`|`PropSet`|
||Adicionador de eventos|`Add`|
||Removedor de eventos|`Remove`|
|Um **operador** composto de duas partes|`op_name`|`NameOp`|
|Por exemplo: operador +|`op_Add`|`AddOp`|
|Para um **operador de conversão**, o tipo retornado é anexado.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Getters e setters de indexadores** são tratados de modo similar à propriedade. O nome padrão de um indexador é `Item`.
> - Os nomes de **tipo de parâmetro** são transformados e concatenados.
> - O **tipo de retorno** é ignorado, a menos que haja uma ambiguidade de sobrecarga. Se houver uma ambiguidade de sobrecarga, o tipo retornado será acrescentado ao final do nome.

### <a name="parameter-type-naming-conventions"></a>Convenções de nomenclatura de tipo de parâmetro

|Fornecido|A cadeia de caracteres acrescentada é...|
|-|-|
|Um **tipo**`T`|T<br /><br /> O namespace, estrutura aninhada e tics genéricos são descartados.|
|Um **parâmetro out**`out T`|`TOut`|
|Um **parâmetro ref** `ref T`|`TRef`|
|Um **tipo de matriz**`T[]`|`TArray`|
|Uma **matriz multidimensional** tipo `T[ , , ]`|`T3`|
|Um **ponteiro** tipo `T*`|`TPtr`|
|Um **tipo genérico**`T<R1, ...>`|`TOfR1`|
|Um **argumento de tipo genérico** `!i` do tipo`C<TType>`|`Ti`|
|Um **argumento de método genérico** `!!i` do método`M<MMethod>`|`Mi`|
|Um **tipo aninhado**`N.T`|`N` é acrescentado, depois `T`|

### <a name="recursive-rules"></a>Regras recursivas

As regras a seguir são aplicadas recursivamente:

- Já que o Fakes usa C# para gerar os assemblies do Fakes, qualquer caractere que produziria um token do C# inválido é escapado para "_" (sublinhado).

- Se um nome resultante corresponde a qualquer membro do tipo declarativo, um esquema de numeração é usado, acrescentando um contador de dois dígitos, começando por 01.

## <a name="see-also"></a>Consulte também

- [Isolamento de código em teste com falsificações da Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)
