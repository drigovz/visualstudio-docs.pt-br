---
title: 'CA1704: Identificadores devem ser escritos corretamente'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dbfc8081f980b7b9e978da782f1627a88a716a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809402"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Identificadores devem ser escritos corretamente

|||
|-|-|
|NomeDoTipo|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

O nome de um identificador contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft. Essa regra não Verifique construtores ou membros de chamada em especial, como obter e definir acessadores de propriedade.

## <a name="rule-description"></a>Descrição da regra

Esta regra analisa o identificador em tokens e verifica a ortografia de cada token. O algoritmo de análise executa as seguintes transformações:

- Letras maiusculas iniciar um novo token. Por exemplo, MyNameIsJoe cria tokens "Meu", "Name", "Is", "Joe".

- Para várias letras maiusculas, a última letra maiuscula inicia um novo token. Por exemplo, GUIEditor cria tokens para "GUI", "Editor".

- À esquerda e à direita apóstrofos são removidos. Por exemplo, 'remetente' cria tokens para "sender".

- Sublinhados significam o final de um token em são removidos. Por exemplo, Hello_world cria tokens para "Hello", "world".

- E comercial inseridos é removidos. Por exemplo, para & mat cria tokens para "formato".

## <a name="language"></a>Idioma

O verificador ortográfico verifica atualmente apenas em relação a dicionários de cultura baseada em inglês. Você pode alterar a cultura do seu projeto no arquivo de projeto, adicionando a **CodeAnalysisCulture** elemento.

Por exemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se você definir a cultura como algo diferente de uma cultura com base em inglês, essa regra de análise de código é silenciosamente desabilitada.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, corrija a grafia da palavra ou adicionar a palavra a um dicionário personalizado.

### <a name="to-add-words-to-a-custom-dictionary"></a>Para adicionar palavras a um dicionário personalizado

Nomeie o arquivo XML de dicionário personalizado *Customdictionary*. Coloque o dicionário no diretório de instalação da ferramenta, o diretório do projeto, ou no diretório que está associado com a ferramenta sob o perfil do usuário (*%USERPROFILE%\Application dados\\...* ). Para saber como adicionar um dicionário personalizado a um projeto no Visual Studio, consulte [como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Adicione palavras que não devem causar uma violação no caminho de dicionário/palavras/reconhecido.

- Adicione palavras que devem causar uma violação no caminho de dicionário/palavras/não reconhecida.

- Adicione palavras que devem ser sinalizadas como obsoletas no caminho de dicionário/palavras/preterido. Consulte o tópico relacionado regra [CA1726: Use termos preferenciais](../code-quality/ca1726-use-preferred-terms.md) para obter mais informações.

- Adicione exceções às regras de maiusculas e minúsculas acrônimo para o caminho de dicionário/acrônimos/CasingExceptions.

Este é um exemplo da estrutura de um arquivo de dicionário personalizado:

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprima um aviso nessa regra somente se a palavra está intencionalmente incorreta e o word aplica-se a um conjunto limitado de biblioteca. Corretamente as palavras escritas de reduzem a curva de aprendizado que é necessária para novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas

- [CA2204: Literais devem ter grafia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Cadeias de caracteres de recurso devem ter grafia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Use termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Consulte também

- [Como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
