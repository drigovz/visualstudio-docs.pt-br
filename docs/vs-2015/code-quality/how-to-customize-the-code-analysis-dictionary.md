---
title: 'Como: personalizar o dicionário de análise de código | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3c8e8005a585e57f61ed873203305517d7b204a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658627"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Como personalizar o dicionário de análise do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A análise de código usa um dicionário interno para verificar identificadores em seu código em busca de erros de ortografia, caso gramatical e outras convenções de nomenclatura das diretrizes de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Você pode criar um arquivo XML de dicionário personalizado para adicionar, remover ou modificar termos, abreviações e acrônimos para o dicionário interno.

 Por exemplo, suponha que seu código continha uma classe chamada **DoorKnokker**. A análise de código identificaria o nome como um composto de duas palavras: **Door** e **knokker**. Em seguida, ele geraria um aviso de que o **knokker** não foi escrito corretamente. Para forçar a análise de código a reconhecer a ortografia, você pode adicionar o termo **knokker** ao dicionário personalizado.

## <a name="to-create-a-custom-dictionary"></a>Para criar um dicionário personalizado
 Crie um arquivo chamado **CustomDictionary. xml**.

 Defina suas palavras personalizadas usando a seguinte estrutura XML:

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Elementos de dicionário personalizados
 Você pode modificar o comportamento do dicionário de análise de código adicionando termos como o texto interno dos seguintes elementos no dicionário personalizado:

- [Dicionário/palavras/reconhecida/palavra](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Dicionário/palavras/não reconhecido/palavra](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Dicionário/palavras/preterido/termo [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dicionário/palavras/composto/termo [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dicionário/palavras/DiscreteExceptions/termo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dicionário/acrônimos/CasingExceptions/acrônimo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="BKMK_DictionaryWordsRecognizedWord"></a>Dicionário/palavras/reconhecida/palavra
 Para incluir um termo na lista de termos que a análise de código identifica como grafada corretamente, adicione o termo como o texto interno de um elemento Dictionary/Words/reconhecidos/palavra-chave. Os termos em dicionário/palavras/reconhecidos/palavras do Word não diferenciam maiúsculas de minúsculas.

 **Exemplo**

```
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Os termos em dicionário/palavras/nós reconhecidos são aplicados às seguintes regras de análise de código:

- [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>Dicionário/palavras/não reconhecido/palavra
 Para excluir um termo da lista de termos que a análise de código identifica como escrita corretamente, adicione o termo a ser excluído como o texto interno de um elemento de dicionário/palavras/não reconhecido/palavra. Os termos em dicionário/palavras/elementos não reconhecidos/de palavras não diferenciam maiúsculas de minúsculas.

 **Exemplo**

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Os termos do nó dicionário/palavras/não reconhecido são aplicados às seguintes regras de análise de código:

- [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Dicionário/palavras/preterido/termo [@PreferredAlternate]
 Para incluir um termo na lista de termos que a análise de código identifica como preterida, adicione o termo como o texto interno de um elemento Dictionary/Words/preterited/Term. Um termo preterido é uma palavra que é digitada corretamente, mas não deve ser usada.

 Para incluir um termo alternativo sugerido no aviso, especifique a alternativa no atributo PreferredAlternate do elemento Term. Você pode deixar o valor do atributo vazio se não quiser sugerir uma alternativa.

- O termo preterido no elemento Dictionary/Words/preterited/Term não diferencia maiúsculas de minúsculas.

- O valor do atributo PreferredAlternate diferencia maiúsculas de minúsculas. Use o caso do Pascal para alternativas compostas.

  **Exemplo**

```
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>

```

 Os termos do nó dicionário/palavras/preterido são aplicados às seguintes regras de análise de código:

- [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)

### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Dicionário/palavras/composto/termo [@CompoundAlternate]
 O dicionário interno identifica alguns termos como termos únicos e discretos, em vez de um termo composto. Para incluir um termo na lista de termos que a análise de código identifica como uma palavra composta e especificar a capitalização correta do termo, adicione o termo como o texto interno de um elemento Dictionary/Words/composto/termo. No atributo CompoundAlternate do elemento Term, especifique as palavras individuais que compõem o termo composto, colocando em maiúscula a primeira letra das palavras individuais (caso Pascal). Observe que o termo especificado no texto interno é adicionado automaticamente à lista Dictionary/Words/DiscreteExceptions.

- O termo preterido no elemento Dictionary/Words/preterited/Term não diferencia maiúsculas de minúsculas.

- O valor do atributo PreferredAlternate diferencia maiúsculas de minúsculas. Use o caso do Pascal para alternativas compostas.

  **Exemplo**

```
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>

```

 Os termos no nó dicionário/palavras/composto são aplicados às seguintes regras de análise de código:

- [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Dicionário/palavras/DiscreteExceptions/termo
 Para excluir um termo na lista de termos que a análise de código identifica como uma única palavra discreta quando o termo é verificado pelas regras de maiúsculas e minúsculas para as palavras compostas, adicione o termo como o texto interno de um elemento Dictionary/Words/DiscreteExceptions/Term. O termo no elemento Dictionary/Words/DiscreteExceptions/Term não diferencia maiúsculas de minúsculas.

 **Exemplo**

```
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>

```

 Os termos no nó Dictionary/Words/DiscreteExceptions são aplicados às seguintes regras de análise de código:

- [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Dicionário/acrônimos/CasingExceptions/acrônimo
 Para incluir um acrônimo na lista de termos que a análise de código identifica como grafada corretamente e para indicar como o acrônimo quando o termo é verificado por regras de maiúsculas e minúsculas para palavras compostas, adicione o termo como o texto interno de um dicionário/acrônimos/CasingExceptions/ Elemento acrônimo. O acrônimo no elemento Dictionary/acrônimos/CasingExceptions/acrônimo diferencia maiúsculas de minúsculas.

 **Exemplo**

```
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>

```

 Os termos no nó Dictionary/acrônimos/CasingExceptions são aplicados às seguintes regras de análise de código:

- [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>Para aplicar um dicionário personalizado a um projeto

1. No **Gerenciador de soluções**, use um dos seguintes procedimentos:

2. Para adicionar um dicionário a um único projeto, clique com o botão direito do mouse no nome do projeto e clique em **Adicionar item existente**. Especifique o arquivo na caixa de diálogo **Adicionar item existente** .

3. Para adicionar um dicionário compartilhado entre dois ou mais projetos, localize o arquivo para compartilhar na caixa de diálogo **Adicionar item existente** , clique na seta para baixo no botão **Adicionar** e, em seguida, clique em **Adicionar como link**.

4. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do arquivo **CustomDictionary. xml** e clique em **Propriedades**.

5. Na lista **ação de compilação** , selecione **CodeAnalysisDictionary**.

6. Na lista **copiar para diretório de saída** , selecione não **copiar**.
