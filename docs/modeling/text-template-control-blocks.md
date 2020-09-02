---
title: Blocos de controle do modelo de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef39e82ea1abe95b3bea799545ed7fbf5b766fd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591782"
---
# <a name="text-template-control-blocks"></a>Blocos de controle do modelo de texto
Os blocos de controle permitem que você escreva código em seu modelo de texto para variar a saída. Há três tipos de blocos de controle, que são diferenciados por seus colchetes de abertura:

- `<# Standard control blocks #>` pode conter instruções.

- `<#= Expression control blocks #>` pode conter expressões.

- `<#+ Class feature control blocks #>` pode conter métodos, campos e propriedades.

## <a name="standard-control-block"></a>Bloco de controle padrão
 Blocos de controle padrão contêm instruções. Por exemplo, o bloco padrão a seguir obtém os nomes de todos os atributos no documento XML:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 Você pode inserir texto sem formatação dentro de uma instrução composta, como `if` ou `for` . Por exemplo, esse fragmento gera uma linha de saída em cada iteração de loop:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> Sempre usar {...} para delimitar instruções aninhadas que contêm texto sem formatação incorporado. O exemplo a seguir pode não funcionar corretamente:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Em vez disso, você deve incluir {colchetes}, da seguinte maneira:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>Bloco de controle de expressão
 Os blocos de controle de expressão são usados para o código que fornece cadeias de caracteres a serem gravadas no arquivo de saída. Por exemplo, com o exemplo acima, você pode imprimir os nomes dos atributos para o arquivo de saída modificando o bloco de código da seguinte maneira:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Bloco de controle de recurso de classe
 Você pode usar blocos de controle de recurso de classe para adicionar métodos, propriedades, campos ou até mesmo classes aninhadas ao seu modelo de texto. O uso mais comum de blocos de recursos de classe é fornecer funções auxiliares para código em outras partes do modelo de texto. Por exemplo, o bloco de recursos de classe a seguir coloca em maiúscula a primeira letra do nome do atributo (ou, se o nome contiver espaço em branco, ele colocará em maiúscula a primeira letra de cada palavra):

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> Um bloco de controle de recurso de classe não deve ser seguido por blocos de controle padrão no mesmo arquivo de modelo. No entanto, essa restrição não se aplica ao resultado do uso de `<#@include#>` diretivas. Cada arquivo incluído pode ter blocos padrão seguidos por blocos de recursos de classe.

 Você pode criar uma função que gera a saída inserindo blocos de texto e de expressão dentro de um bloco de controle de recurso de classe. Por exemplo:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Você poderia chamar essa função de um bloco Standard ou de outro bloco de recursos de classe:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Como usar blocos de controle
 Todo o código em todos os blocos de controle Standard e Expression em um único modelo (incluindo todo o código em modelos incluídos) é combinado para formar o `TransformText()` método do código gerado. (Para obter mais informações sobre como incluir outros modelos de texto com a `include` diretiva, consulte [diretivas de modelo de texto T4](../modeling/t4-text-template-directives.md).)

 Você deve ter em mente as seguintes considerações ao usar blocos de controle:

- **Idioma.** Você pode usar o código C# ou Visual Basic em um modelo de texto. O idioma padrão é C#, mas você pode especificar Visual Basic com o `language` parâmetro da `template` diretiva. (Para obter mais informações sobre a `template` diretiva, consulte [diretivas de modelo de texto T4](../modeling/t4-text-template-directives.md).)

     O idioma usado em blocos de controle não tem nada a ver com o idioma ou o formato do texto que você gera em um modelo de texto. Você pode gerar C# usando Visual Basic código ou vice-versa.

     Você pode usar apenas um idioma em um determinado modelo de texto, incluindo todos os modelos de texto que você inclui com a `include` diretiva.

- **Variáveis locais.** Como todo o código nos blocos de controle Standard e Expression em um modelo de texto é gerado como um único método, você deve certificar-se de que não há conflitos com os nomes das variáveis locais. Se você estiver incluindo outros modelos de texto, deverá certificar-se de que os nomes de variáveis sejam exclusivos em todos os modelos incluídos. Uma maneira de garantir isso é adicionar uma cadeia de caracteres a cada nome de variável local identificando o modelo de texto no qual ele foi declarado.

     Também é uma boa ideia inicializar suas variáveis locais para valores razoáveis ao declará-las, especialmente quando você estiver incluindo vários modelos de texto.

- **Aninhamento de blocos de controle.** Blocos de controle não podem ser aninhados dentro uns dos outros. Você sempre deve encerrar um determinado bloco de controle antes de abrir outro. Por exemplo, veja a seguir como imprimir um texto em um bloco de expressão como parte de um bloco de controle padrão.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refatoração.** Para manter seus modelos de texto curtos e fáceis de entender, é altamente recomendável que você evite código repetitivo, fatorando o código reutilizável em funções auxiliares em blocos de recursos de classe ou criando sua própria classe de modelo de texto que herda da classe Microsoft. VisualStudio. TextTemplating. TextTransformation.
