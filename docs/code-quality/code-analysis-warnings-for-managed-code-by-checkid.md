---
title: Visão geral das regras de qualidade de código
ms.date: 09/01/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a298ab142ae6a44c1fb24b2cb1b752f6beb4a68e
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037231"
---
# <a name="code-quality-analysis-rules-by-rule-id"></a>Regras de análise de qualidade de código por ID de regra

A tabela a seguir lista as regras de análise de qualidade de código por identificador de regra.

| CheckId | Aviso | Descrição |
|---------| - | - |
| CA1000 | [CA1000: Não declarar membros estáticos em tipos genéricos](../code-quality/ca1000.md) | Quando um membro estático de um tipo genérico é chamado, o argumento de tipo deve ser especificado para o tipo. Quando um membro de instância genérico que não dá suporte à inferência é chamado, o argumento de tipo deve ser especificado para o membro. Nesses dois casos, a sintaxe para especificar o argumento de tipo é diferente e facilmente confundida. |
| CA1001 | [CA1001: Tipos com campos descartáveis devem ser descartáveis](../code-quality/ca1001.md) | Uma classe declara e implementa um campo de instância que é um tipo System.IDisposable, e a classe não implementa IDisposable. Uma classe que declara um campo IDisposable indiretamente possui um recurso não gerenciado e deve implementar a interface IDisposable. |
| CA1002 | [CA1002: Não expor listas genéricas](../code-quality/ca1002.md) | System. Collections. Generic. List< (Of \<(T> ) >) é uma coleção genérica projetada para desempenho, não herança. Por isso, List não contém membros virtuais. As coleções genéricas projetadas para herança devem ser expostas em seu lugar. |
| CA1003 | [CA1003: Usar instâncias do manipulador de eventos genérico](../code-quality/ca1003.md) |Um tipo contém um representante que retorna nulo, cuja assinatura contém dois parâmetros (o primeiro um objeto e o segundo um tipo atribuível a EventArgs), e o destino do assembly de contenção é o Microsoft .NET Framework 2.0. |
| CA1005 | [CA1005: Evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005.md) | Quanto mais parâmetros de tipo um tipo genérico contiver, mais difícil será saber e lembrar-se do que cada parâmetro de tipo representa. Normalmente, isso é óbvio com um parâmetro de tipo, como na lista \<T> e, em determinados casos, com dois parâmetros de tipo, como no dicionário \<TKey, TValue> . No entanto, se houver mais de dois parâmetros de tipo, a dificuldade ficará muito grande para a maioria dos usuários. |
| CA1008 | [CA1008: Enumerações devem ter valor zero](../code-quality/ca1008.md) | O valor padrão de uma enumeração não inicializada, assim como o de outros tipos de valor, é zero. Uma enumeração atribuída por nonflags deve definir um membro usando o valor de zero de forma que o valor padrão seja um valor válido da enumeração. Se uma enumeração que tem o atributo FlagsAttribute aplicado definir um membro com valor, seu nome deverá ser “None” para indicar que nenhum valor foi definido na enumeração. |
| CA1010 | [CA1010: Coleções devem implementar uma interface genérica](../code-quality/ca1010.md) | Para ampliar a usabilidade de uma coleção, implemente uma das interfaces da coleção genéricas. Em seguida, a coleção pode ser usada para popular tipos de coleção genéricos. |
| CA1012 | [CA1012: Tipos abstratos não devem ter construtores](../code-quality/ca1012.md) | Construtores em tipos abstratos só podem ser chamados por tipos derivados. Como construtores públicos criam instâncias de um tipo e não é possível criar instâncias de um tipo abstrato, um tipo abstrato com um construtor público é projetado incorretamente. |
| CA1014 | [CA1014: Marcar assemblies com CLSCompliantAttribute](../code-quality/ca1014.md) | A CLS (Common Language Specification) define restrições de nomenclatura, tipos de dados e regras que assemblies deverão respeitar se forem usados em todas as linguagens de programação. Um bom design determina que todos os assemblies indiquem explicitamente a conformidade com CLS usando-se <xref:System.CLSCompliantAttribute>. Se esse atributo não estiver presente em um assembly, o assembly não será compatível. |
| CA1016 | [CA1016: Marcar assemblies com AssemblyVersionAttribute](../code-quality/ca1016.md) | O .NET usa o número de versão para identificar exclusivamente um assembly e associar a tipos em assemblies com nomes de alta segurança. O número de versão é usado com a versão e a política do publicador. Por padrão, os aplicativos só são executados com a versão do assembly com que foram criados. |
| CA1017 | [CA1017: Marcar assemblies com ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute determina como clientes COM acessam código gerenciado. Um bom design determina que os assemblies indiquem explicitamente a visibilidade de COM. A visibilidade de COM pode ser definida para todo o assembly e, em seguida, substituída por tipos individuais e membros de tipo. Caso esse atributo não esteja presente, o conteúdo do assembly permanece visível aos clientes COM. |
| CA1018 | [CA1018: Marcar atributos com AttributeUsageAttribute](../code-quality/ca1018.md) | Ao definir um atributo personalizado, você o marca usando AttributeUsageAttribute para indicar onde o atributo personalizado pode ser aplicado no código-fonte. O significado e o uso desejado de um atributo determinarão seus locais válidos no código. |
| CA1019 | [CA1019: Definir acessadores para argumentos de atributo](../code-quality/ca1019.md) | Os atributos podem definir argumentos obrigatórios que devem ser especificados quando você aplica o atributo a um destino. Eles também são conhecidos como argumentos posicionais porque são fornecidos a construtores de atributos como parâmetros posicionais. Para cada argumento obrigatório, o atributo também deve fornecer uma propriedade somente leitura correspondente de forma que o valor do argumento possa ser recuperado no tempo de execução. Os atributos também podem definir argumentos opcionais, que também são conhecidos como argumentos nomeados. Esses argumentos são fornecidos a construtores de atributo por nome e devem ter uma propriedade de leitura/gravação correspondente. |
| CA1021 | [CA1021: Evitar parâmetros out](../code-quality/ca1021.md) | A passagem de tipos por referência (usando out ou ref) requer experiência com ponteiros, compreensão das diferenças entre tipos de valor e tipos de referência e os métodos de tratamento com vários valores de retorno. Além disso, a diferença entre parâmetros out e ref não é amplamente compreendida. |
| CA1024 | [CA1024: Usar propriedades quando apropriado](../code-quality/ca1024.md) | Um método público ou protegido tem um nome que começa com "Get", não utiliza parâmetros e retorna um valor que não é uma matriz. O método pode ser um bom candidato a se tornar uma propriedade. |
| CA1027 |[CA1027: Marcar enumerações com FlagsAttribute](../code-quality/ca1027.md) | Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Aplique FlagsAttribute a uma enumeração quando suas constantes nomeadas puderem ser combinadas de maneira significativa. |
| CA1028 | [CA1028: O armazenamento de enumerações deve ser Int32](../code-quality/ca1028.md) | Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Por padrão, o tipo de dados System.Int32 é usado para armazenar o valor constante. Embora seja possível alterar esse tipo subjacente, isso não é necessário ou recomendado na maioria dos cenários. |
| CA1030 | [CA1030: Usar eventos quando apropriado](../code-quality/ca1030.md) |Essa regra detecta métodos que têm nomes que seriam usados normalmente em eventos. Se um método for chamado em resposta a uma alteração de estado claramente definida, o método deverá ser invocado por um manipulador de eventos. Os objetos que chamam o método devem acionar eventos, em vez de chamar o método diretamente. |
| CA1031 | [CA1031: Não capturar tipos de exceção geral](../code-quality/ca1031.md) | As exceções gerais não devem ser capturadas. Capture uma exceção mais específica ou relance a exceção geral como a última instrução no bloco de captura. |
| CA1032 |[CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032.md) | Deixar de fornecer o conjunto completo de construtores pode dificultar o tratamento correto das exceções. |
| CA1033 | [CA1033: Métodos de interface devem ser chamados por tipos filho](../code-quality/ca1033.md) | Um tipo visível externamente sem lacre fornece uma implementação de método explícita de uma interface pública e não fornece um método visível externamente alternativo com o mesmo nome. |
| CA1034 | [CA1034: Tipos aninhados não devem ser visíveis](../code-quality/ca1034.md) | Um tipo aninhado é um tipo declarado no escopo de outro tipo. Os tipos aninhados são úteis para encapsular detalhes de implementação privados do tipo de contenção. Usados para essa finalidade, os tipos aninhados não devem ser visíveis externamente. |
| CA1036 | [CA1036: Substituir métodos em tipos comparáveis](../code-quality/ca1036.md) |Um público ou um tipo protegido implementa a interface System.IComparable. Ele não substitui Object.Equals nem sobrecarrega o operador específico da linguagem para igualdade, desigualdade, menor que ou maior que. |
| CA1040 |[CA1040: Evitar interfaces vazias](../code-quality/ca1040.md) | As interfaces definem os membros que fornecem um contrato de comportamento ou de uso. A funcionalidade descrita pela interface pode ser adotada por qualquer tipo, independentemente de onde o tipo seja exibido na hierarquia de herança. Um tipo implementa uma interface fornecendo implementações para os membros da interface. Uma interface vazia não define membros; por isso, ela não define um contrato que pode ser implementado. |
| CA1041 | [CA1041: Fornecer a mensagem ObsoleteAttribute](../code-quality/ca1041.md) | Um tipo ou um membro é marcado usando-se um atributo System.ObsoleteAttribute que não tem sua propriedade ObsoleteAttribute.Message especificada. Quando um tipo ou um membro marcado usando-se ObsoleteAttribute é compilado, a propriedade Message do atributo é exibida. Isso dá ao usuário informações sobre o tipo ou o membro obsoleto. |
| CA1043 | [CA1043: Usar argumento integral ou de cadeia de caracteres para indexadores](../code-quality/ca1043.md) | Os indicadores (ou seja, propriedades indexadas) devem usar tipos integrais ou de cadeia de caracteres no índice. Esses tipos normalmente são usados na indexação de estruturas de dados e aumentam a usabilidade da biblioteca. O uso do tipo Object deve ser restrito a esses casos em que o tipo integral ou de cadeia de caracteres específico não pode ser especificado no tempo de design. |
| CA1044 | [CA1044: Propriedades não devem ser somente gravação](../code-quality/ca1044.md) | Embora seja aceitável e normalmente necessário ter uma propriedade somente leitura, as diretrizes de design proíbem o uso de propriedades somente gravação. Isso é porque a permissão para que um usuário defina um valor e o impedimento posterior para ele exiba esse valor não dão nenhuma segurança. Além disso, sem acesso de leitura, o estado de objetos compartilhados não pode ser exibido, o que limita sua utilidade. |
| CA1045 |[CA1045: Não passar tipos por referência](../code-quality/ca1045.md) | A passagem de tipos por referência (usando out ou ref) requer experiência com ponteiros, compreensão das diferenças entre tipos de valor e tipos de referência e os métodos de tratamento que têm vários valores de retorno. Os arquitetos de biblioteca que projetam um público geral não devem esperar que os usuários façam o mestre de trabalho com os `out` `ref` parâmetros ou. |
| CA1046 | [CA1046: Não sobrecarregar o operador equals em tipos de referência](../code-quality/ca1046.md) | Para tipos de referência, a implementação padrão do operador de igualdade está quase sempre correta. Por padrão, duas referências só serão iguais se apontarem para o mesmo objeto. |
| CA1047 |[CA1047: Não declarar membros protegidos em tipos selados](../code-quality/ca1047.md) | Os tipos declaram membros protegidos de forma que a herança de tipos possa acessar ou substituir o membro. Por definição, os tipos vedados não podem ser lacrados, o que significa que os métodos protegidos em tipos lacrados não podem ser chamados. |
| CA1050 | [CA1050: Declarar tipos em namespaces](../code-quality/ca1050.md) | Tipos são declarados em namespaces para evitar conflitos de nome e são uma maneira de organizar tipos relacionados em uma hierarquia de objetos. |
| CA1051 | [CA1051: Não declarar campos de instância visíveis](../code-quality/ca1051.md) | O principal uso de um campo deve ser um como um detalhe da implementação. Os campos devem ser privados ou internos e devem ser expostos usando-se propriedades. |
| CA1052 | [CA1052: Tipos de suporte estático devem ser selados](../code-quality/ca1052.md) | Um tipo público ou protegido contém apenas membros estáticos e não é declarado usando-se o modificador (Reference do C#) (NotInheritable). Um tipo que não é deve ser herdado deve ser marcado usando-se o modificador lacrado para evitar seu uso como um tipo de base. |
| CA1053 |[CA1053: Tipos de suporte estático não devem ter construtores](../code-quality/ca1053.md) | Um tipo público ou público aninhado declara apenas membros estáticos e tem um construtor padrão público ou protegido. O construtor é desnecessário porque chamar membros estáticos não exige uma instância do tipo. A sobrecarga de cadeia de caracteres deve chamar a sobrecarga do URI (Uniform Resource Identifier) usando-se o argumento de cadeia de caracteres por questões de segurança. |
| CA1054 | [CA1054: Parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054.md) | Se um método utilizar uma representação de cadeia de caracteres de um URI, uma sobrecarga correspondente deverá ser fornecida utilizando uma instância da classe do URI, que oferece esses serviços de maneira segura e protegida. |
| CA1055 | [CA1055: Valores de retorno de URI não devem ser cadeias de caracteres](../code-quality/ca1055.md) | Esta regra pressupõe que o método retorne um URI. Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A classe System.Uri fornece esses serviços de maneira segura. |
| CA1056 | [CA1056: Propriedades de URI não devem ser cadeias de caracteres](../code-quality/ca1056.md) | Esta regra pressupõe que a propriedade represente o URI. Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A classe System.Uri fornece esses serviços de maneira segura. |
| CA1058 | [CA1058: Tipos não devem estender determinados tipos base](../code-quality/ca1058.md) | Um tipo visível externamente estende determinados tipos de base. Use uma das alternativas. |
| CA1060 | [CA1060: mover P/Invokes para a classe NativeMethods](../code-quality/ca1060.md) | Métodos de invocação da plataforma, como os marcados usando-se o atributo System.Runtime.InteropServices.DllImportAttribute, ou métodos definidos usando-se a palavra-chave Declare em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], acessam um código não gerenciado. Esses métodos devem ser da classe NativeMethods, SafeNativeMethods ou UnsafeNativeMethods. |
| CA1061 |[CA1061: Não ocultar métodos de classe base](../code-quality/ca1061.md) | Um método em um tipo de base permanece oculto por um método nomeado identicamente em um tipo derivado, quando a assinatura do parâmetro do método derivado difere apenas pelos tipos derivados de maneira mais fraca do que os tipos correspondentes na assinatura do parâmetro do método de base. |
| CA1062 | [CA1062: Validar argumentos de métodos públicos](../code-quality/ca1062.md) | Todos os argumentos de referência passados para os métodos visíveis externamente devem ser verificados em relação que serão nulos. |
| CA1063 | [CA1063: Implementar IDisposable corretamente](../code-quality/ca1063.md) | Todos os tipos IDisposable devem implementar o padrão Dispose corretamente. |
| CA1064 | [CA1064: Exceções devem ser públicas](../code-quality/ca1064.md) | Uma exceção interna só permanece visível dentro do próprio escopo interno. Depois que a exceção falha fora do escopo interno, somente a exceção de base pode ser usada para capturar a exceção. Se a exceção interna for herdada de <xref:System.Exception> , <xref:System.SystemException> ou <xref:System.ApplicationException> , o código externo não terá informações suficientes para saber o que fazer com a exceção. |
| CA1065 | [CA1065: Não acionar exceções em locais inesperados](../code-quality/ca1065.md) | Um método que não deve acionar exceções aciona uma exceção. |
| CA1066 | [CA1066: Implementar IEquatable ao substituir Equals](../code-quality/ca1066.md) | Um tipo de valor substitui o <xref:System.Object.Equals%2A> método, mas não <xref:System.IEquatable%601> implementa. |
| CA1067 | [CA1067: Substituir Equals ao implementar IEquatable](../code-quality/ca1067.md) | Um tipo implementa <xref:System.IEquatable%601> , mas não substitui o <xref:System.Object.Equals%2A> método. |
| CA1068 | [CA1068: Os parâmetros CancellationToken devem vir por último](../code-quality/ca1068.md) | Um método tem um parâmetro CancellationToken que não é o último parâmetro. |
| CA1069 | [CA1069: Enumerações não devem ter valores duplicados](../code-quality/ca1069.md) | Uma enumeração tem vários membros que são atribuídos explicitamente ao mesmo valor de constante. |
| CA1070 | [CA1070: Não declarar os campos de evento como virtuais](../code-quality/ca1070.md) | Um [evento do tipo campo](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) foi declarado como virtual. |
| CA1200 | [CA1200: Evitar o uso de marcas cref com um prefixo](../code-quality/ca1200.md) | O atributo [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) em uma marca de documentação XML significa "referência de código". Ele especifica que o texto interno da marca é um elemento de código, como um tipo, método ou propriedade. Evite usar `cref` marcas com prefixos, pois isso impede que o compilador Verifique as referências. Ele também impede que o IDE (ambiente de desenvolvimento integrado) do Visual Studio Localize e atualize essas referências de símbolo durante refatoração. |
| CA1303 | [CA1303: Não passar literais como parâmetros localizados](../code-quality/ca1303.md) | Um método visível externamente passa um literal de cadeia de caracteres como um parâmetro para um construtor ou método .NET, e essa cadeia de caracteres deve ser localizável. |
| CA1304 | [CA1304: Especificar CultureInfo](../code-quality/ca1304.md) | Um método ou um construtor chama um membro que tem uma sobrecarga que aceita um parâmetro System.Globalization.CultureInfo, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro CultureInfo. Quando um objeto CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades. |
| CA1305 | [CA1305: Especificar IFormatProvider](../code-quality/ca1305.md) | Um método ou um construtor chama um ou mais membros que têm sobrecargas que aceitam um parâmetro System.IFormatProvider, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro IFormatProvider. Quando um objeto System.Globalization.CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades. |
| CA1307 | [CA1307: Especificar StringComparison para garantir a clareza](../code-quality/ca1307.md) | Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro StringComparison. |
| CA1308 |[CA1308: Normalizar cadeias de caracteres em maiúsculas](../code-quality/ca1308.md) | As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres não pode fazer uma viagem de ida e volta quando são convertidos em minúsculas. |
| CA1309 | [CA1309: Usar StringComparison ordinal](../code-quality/ca1309.md) | Uma operação de comparação de cadeia de caracteres não linguística não define o parâmetro StringComparison como Ordinal ou OrdinalIgnoreCase. Definindo-se explicitamente o parâmetro como StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, o código normalmente ganha velocidade, fica mais correto e se torna mais confiável. |
| CA1310 | [CA1310: Especificar StringComparison para garantir a exatidão](../code-quality/ca1310.md) | Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro StringComparison e usa a comparação de cadeia de caracteres específica de cultura por padrão. |
| CA1401 | [CA1401: P/Invokes não devem estar visíveis](../code-quality/ca1401.md) | Um método público ou protegido em um tipo público tem o atributo System.Runtime.InteropServices.DllImportAttribute (também implementado pela palavra-chave Declare em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Esses métodos não devem ser expostos. |
| CA1417 | [CA1417: não usar `OutAttribute` em parâmetros de cadeia de caracteres para P/Invokes](../code-quality/ca1417.md) | Parâmetros de cadeia de caracteres passados por valor com o `OutAttribute` podem desestabilizar o tempo de execução se a cadeia de caracteres for uma cadeia de caracteres interna. |
| CA1501 | [CA1501: Evitar herança excessiva](../code-quality/ca1501.md) | Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter. |
| CA1502 | [CA1502: Evitar complexidade excessiva](../code-quality/ca1502.md) | Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais. |
| CA1505 | [CA1505: Evitar código de difícil manutenção](../code-quality/ca1505.md) | Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design. |
| CA1506 | [CA1506: Evitar acoplamento de classes excessivo](../code-quality/ca1506.md) | Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém. |
| CA1507 | [CA1507: Usar nameof no lugar da cadeia de caracteres](../code-quality/ca1507.md) | Um literal de cadeia de caracteres é usado como um argumento em que uma `nameof` expressão pode ser usada. |
| CA1508 | [CA1508: Evitar código condicional morto](../code-quality/ca1508.md) | Um método tem código condicional que sempre é avaliado como `true` ou `false` em tempo de execução. Isso leva a um código inativo na `false` ramificação da condição. |
| CA1509 | [CA1509: Entrada inválida no arquivo de configuração de métrica de código](../code-quality/ca1509.md) | As regras de métricas de código, como [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) e [CA1506](ca1506.md), forneciam um arquivo de configuração chamado `CodeMetricsConfig.txt` que tem uma entrada inválida. |
| CA1700 | [CA1700: Não nomear valores de enumeração 'Reserved'](../code-quality/ca1700.md) | Esta regra pressupõe que um membro da enumeração que tenha um nome que contém "reserved" não é usado atualmente, mas é um espaço reservado a ser renomeado ou removido em uma versão futura. Renomear ou remover um membro é uma alteração drástica. |
| CA1707 | [CA1707: Identificadores não devem conter sublinhados](../code-quality/ca1707.md) | Por convenção, os nomes de identificador não contêm o caractere de sublinhado (_). Esta regra verifica namespaces, tipos, membros e parâmetros. |
| CA1708 | [CA1708: Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas](../code-quality/ca1708.md) | Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas. |
| CA1710 | [CA1710: Identificadores devem ter um sufixo correto](../code-quality/ca1710.md) |Por convenção, os nomes de tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, têm um sufixo associado ao tipo de base ou à interface. |
| CA1711 | [CA1711: Identificadores não devem ter um sufixo incorreto](../code-quality/ca1711.md) | Por convenção, apenas os nomes de tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, devem terminar com sufixos reservados específicos. Outros nomes de tipo não devem usar esses sufixos reservados. |
| CA1712 | [CA1712: Não prefixar valores de enumeração com um nome de tipo](../code-quality/ca1712.md) | Os nomes dos membros de enumeração não são prefixados usando-se o nome de tipo porque as ferramentas de desenvolvimento devem fornecer informações de tipo. |
| CA1713 | [CA1713: Eventos não devem ter o prefixo anterior ou posterior](../code-quality/ca1713.md) | O nome de um evento começa com "Before" ou "After". Para nomear eventos relacionados acionados em uma sequência específica, use o presente ou o pretérito para indicar a posição relativa na sequência de ações. |
| CA1714 | [CA1714: Enumerações de sinalizador devem ter nomes no plural](../code-quality/ca1714.md) | Uma enumeração pública tem o atributo System.FlagsAttribute, e seu nome não termina com "s". Tipos marcados usando FlagsAttribute têm nomes que estão no plural porque o atributo indica que mais de um valor pode ser especificado. |
| CA1715 | [CA1715: Identificadores devem ter um prefixo correto](../code-quality/ca1715.md) | O nome de uma interface visível externamente não começa com "I" em maiúsculas. O nome de um parâmetro de tipo genérico em um tipo visível externamente ou método não começa com um "T" em maiúsculas. |
| CA1716 | [CA1716: Identificadores não devem corresponder a palavras-chave](../code-quality/ca1716.md) | Um nome de namespace ou um nome de tipo corresponde a uma palavra-chave reservada em uma linguagem de programação. Os identificadores de namespaces e tipos não devem corresponder a palavras-chave definidas por com o Common Language Runtime como destino. |
| CA1717 | [CA1717: Apenas enumerações FlagsAttribute devem ter nomes no plural](../code-quality/ca1717.md) | As convenções de nomenclatura determinam que um nome no plural para uma enumeração indica que mais de um valor de enumeração pode ser especificado ao mesmo tempo. |
| CA1720 |[CA1720: Identificadores não devem conter nomes de tipos](../code-quality/ca1720.md) | O nome de um parâmetro em um membro visível externamente contém um nome de tipo de dados, ou o nome de um membro visível externamente contém um nome de tipo de dados específico da linguagem. |
| CA1721 | [CA1721: Nomes de propriedades não devem corresponder a métodos get](../code-quality/ca1721.md) |O nome de um membro público ou protegido começa com "Get" e, de outra forma, corresponde ao nome de uma propriedade pública ou protegida. Métodos "Get" e propriedades devem ter nomes que diferenciem claramente a função. |
| CA1724 | [CA1724: Nomes de tipos não devem corresponder a namespaces](../code-quality/ca1724.md) | Os nomes de tipo não devem corresponder aos nomes dos namespaces do .NET. A violação dessa regra pode reduzir a usabilidade da biblioteca. |
| CA1725 | [CA1725: Nomes de parâmetros devem corresponder à declaração base](../code-quality/ca1725.md) | A nomenclatura consistente dos parâmetros em uma hierarquia de substituição aumenta a usabilidade das substituições de método. Um nome de parâmetro em um método derivado diferente do nome na declaração de base pode causar confusão em relação à possibilidade do método ser uma substituição do método de base ou de uma nova sobrecarga do método. |
| CA1801 | [CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801.md) | Uma assinatura de método inclui um parâmetro que não é usado no corpo do método. |
| CA1802 |[CA1802: Usar literais quando apropriado](../code-quality/ca1802.md) |Um campo é declarado estático e somente leitura (Shared e ReadOnly no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), e é inicializado usando-se um valor computável no tempo de compilação. Como o valor atribuído ao campo de destino é computáveis em tempo de compilação, altere a declaração para um campo const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) para que o valor seja calculado em tempo de compilação em vez de em tempo de execução. |
| CA1805 | [CA1805: Não inicializar desnecessariamente](../code-quality/ca1805.md) | O tempo de execução do .NET inicializa todos os campos de tipos de referência para seus valores padrão antes de executar o construtor. Na maioria dos casos, a inicialização explícita de um campo para seu valor padrão é redundante, o que aumenta os custos de manutenção e pode prejudicar o desempenho (como com o maior tamanho do assembly). |
| CA1806 | [CA1806: Não ignorar resultados do método](../code-quality/ca1806.md) | Um novo objeto é criado, mas nunca é usado; ou um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres jamais é usada; um método ou COM ou P/Invoke retorna um HRESULT ou um código de erro que nunca é usado. |
| CA1810 | [CA1810: Inicializar campos estáticos de tipo de referência em linha](../code-quality/ca1810.md) | Quando um tipo declara um construtor estático explícito, o compilador JIT (just-in-time) adiciona uma verificação a cada método estático e construtor de instância do tipo para garantir que o construtor estático tenha sido chamado anteriormente. As verificações de construtor estático podem diminuir o desempenho. |
| CA1812 | [CA1812: Evitar classes internas sem instâncias](../code-quality/ca1812.md) | Uma instância de um tipo no nível de assembly não é criada pelo código no assembly. |
| CA1813 | [CA1813: Evitar atributos não selados](../code-quality/ca1813.md) | O .NET fornece métodos para recuperar atributos personalizados. Por padrão, esses métodos pesquisam a hierarquia de herança do atributo. A validação do atributo elimina a pesquisa na hierarquia de herança e pode melhorar o desempenho. |
| CA1814 | [CA1814: Preferir matrizes denteadas a matrizes multidimensionais](../code-quality/ca1814.md) | Uma matriz denteada é uma matriz cujos elementos são matrizes. As matrizes que constituem os elementos podem ter tamanhos diferentes, o que leva a menos espaço desperdiçado para alguns conjuntos de dados. |
| CA1815 | [CA1815: Substituir equals e o operador equals em tipos de valor](../code-quality/ca1815.md) | Para tipos de valor, a implementação herdada de Equals usa a biblioteca Reflection e compara o conteúdo de todos os campos. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários comparem ou classifiquem instâncias, ou usem instâncias como chaves de tabela de hash, o tipo de valor deverá implementar Equals. |
| CA1816 | [CA1816: Chamar GC.SuppressFinalize corretamente](../code-quality/ca1816.md) | Um método que é uma implementação de Dispose não chama GC.SuppressFinalize; ou um método que não é uma implementação de Dispose chama GC.SuppressFinalize; ou um método chama GC.SuppressFinalize e passa algo que não seja isso (Me no Visual Basic). |
| CA1819 | [CA1819: Propriedades não devem retornar matrizes](../code-quality/ca1819.md) | As matrizes retornadas por propriedades não estão protegidas contra a gravação, mesmo quando a propriedade é somente leitura. Para manter a matriz à prova de adulteração, a propriedade deve retornar uma cópia da matriz. Normalmente, os usuários não compreenderão as implicações adversas no desempenho de chamar uma propriedade assim. |
| CA1820 | [CA1820: Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres](../code-quality/ca1820.md) | A comparação de cadeias de caracteres usando-se a propriedade String.Length ou o método String.IsNullOrEmpty é significativamente mais rápida do que o uso de Equals. |
| CA1821 | [CA1821: Remover finalizadores vazios](../code-quality/ca1821.md) | Sempre que possível, evite finalizadores por conta da sobrecarga adicional no desempenho envolvida no acompanhamento do tempo de vida do objeto. Um finalizador vazio incorre na sobrecarga adicionada e não oferece benefícios. |
| CA1822 |[CA1822: Marcar membros como estáticos](../code-quality/ca1822.md) | Os membros que não acessam dados da instância ou os métodos da instância de chamada podem ser marcados como estáticos (Shared no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Depois que você marcar os métodos como estáticos, o compilador emitirá sites de chamada não virtuais para esses membros. Isso pode proporcionar um ganho de desempenho mensurável para o código sensível ao desempenho. |
| CA1823 | [CA1823: Evitar campos particulares não utilizados](../code-quality/ca1823.md) | Foram detectados campos particulares que aparentemente não são acessados no assembly. |
| CA1824 |[CA1824: Marque assemblies com NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | O atributo NeutralResourcesLanguage informa o Gerenciador de recursos da linguagem que foi usada para exibir os recursos de uma cultura neutra para um assembly. Isso melhora o desempenho da pesquisa para o primeiro recurso carregado e pode reduzir o conjunto de trabalho. |
| CA1825 |[CA1825: Evitar alocações de matriz de comprimento zero](../code-quality/ca1825.md) | A inicialização de uma matriz de comprimento zero leva à alocação de memória desnecessária. Em vez disso, use a instância de matriz vazia estaticamente alocada chamando <xref:System.Array.Empty%2A?displayProperty=nameWithType> . A alocação de memória é compartilhada entre todas as invocações desse método. |
| CA1826 |[CA1826: Usar a propriedade em vez do método Linq Enumerable](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> O método LINQ foi usado em um tipo que dá suporte a uma propriedade equivalente e mais eficiente. |
| CA1827 |[CA1827: Não usar Count/LongCount quando Any puder ser usado](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> o <xref:System.Linq.Enumerable.LongCount%2A> método or foi usado onde o <xref:System.Linq.Enumerable.Any%2A> método seria mais eficiente. |
| CA1828 |[CA1828: Não usar CountAsync/LongCountAsync quando AnyAsync puder ser usado](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> o <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> método or foi usado onde o <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> método seria mais eficiente. |
| CA1829 |[CA1829: Usar a propriedade Length/Count em vez do método Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> O método LINQ foi usado em um tipo que dá suporte a uma propriedade equivalente, mais eficiente `Length` ou `Count` . |
| CA1830 |[CA1830: Preferir os métodos Acrescentar e Inserir fortemente tipados provoca uma sobrecarga no StringBuilder](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> e <xref:System.Text.StringBuilder.Insert%2A> fornecem sobrecargas para vários tipos além do <xref:System.String> .  Quando possível, prefira as sobrecargas fortemente tipadas usando ToString () e a sobrecarga baseada em cadeia de caracteres. |
| CA1831 |[CA1831: Usar AsSpan em vez de indexadores baseados em intervalo na cadeia de caracteres quando apropriado](../code-quality/ca1831.md) | Ao usar um indexador de intervalo em uma cadeia de caracteres e atribuir implicitamente o valor ao &lt; tipo de Char ReadOnlySpan &gt; , o método <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> será usado em vez de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , que produz uma cópia da parte solicitada da cadeia de caracteres. |
| CA1832 |[CA1832: Usar AsSpan ou AsMemory em vez de indexadores baseados em intervalo para obter a parte ReadOnlySpan ou ReadOnlyMemory de uma matriz](../code-quality/ca1832.md) | Ao usar um indexador de intervalo em uma matriz e atribuir implicitamente o valor a um <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> tipo ou, o método <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> será usado em vez de, o <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> que produzirá uma cópia da parte solicitada da matriz. |
| CA1833 |[CA1833: Usar AsSpan ou AsMemory em vez de indexadores baseados em intervalo para obter a parte Span ou Memory de uma matriz](../code-quality/ca1833.md) | Ao usar um indexador de intervalo em uma matriz e atribuir implicitamente o valor a um <xref:System.Span%601> <xref:System.Memory%601> tipo ou, o método <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> será usado em vez de, o <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> que produzirá uma cópia da parte solicitada da matriz. |
| CA1834 |[CA1834: usar StringBuilder.Append (char) para cadeias de caracteres únicas](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> tem uma `Append` sobrecarga que usa `char` como argumento. Prefira chamar a `char` sobrecarga por motivos de desempenho. |
| CA1835 |[CA1835: prefira as sobrecargas baseadas em Memory' para ' ReadAsync ' e ' WriteAsync '](../code-quality/ca1835.md) | ' Stream ' tem uma sobrecarga ' ReadAsync ' que usa um ' byte de memória &lt; &gt; ' como o primeiro argumento e uma sobrecarga ' WriteAsync ' que usa um ' ReadOnlyMemory &lt; byte &gt; ' como o primeiro argumento. Prefira chamar as sobrecargas com base na memória, que são mais eficientes. |
| CA1836 |[CA1836: preferir `IsEmpty` `Count` quando disponível](../code-quality/ca1836.md) | Prefira `IsEmpty` a propriedade que seja mais eficiente do que `Count` , `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> ou <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> para determinar se o objeto contém ou não itens. |
| CA1837 | [CA1837: usar `Environment.ProcessId` em vez de `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` é mais simples e mais rápido do que `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: Evite `StringBuilder` parâmetros para P/Invokes](../code-quality/ca1838.md) | O marshaling de ' StringBuilder ' sempre cria uma cópia de buffer nativo, resultando em várias alocações para uma operação de marshaling. |
| CA2000 | [CA2000: Descartar objetos antes de perder o escopo](../code-quality/ca2000.md) | Como pode ocorrer um evento excepcional que impedirá a execução do finalizador de um objeto, o objeto deve ser explicitamente descartado antes que todas as referências a ele estejam fora do escopo. |
| CA2002 |[CA2002: Não bloquear objetos com identidade fraca](../code-quality/ca2002.md) |Diz-se que um objeto tem uma identidade fraca quando puder ser acessado diretamente em todos os limites de domínio do aplicativo. Um thread que tente adquirir um bloqueio em um objeto com uma identidade fraca pode ser bloqueado por um segundo thread em um domínio de aplicativo diferente com um bloqueio no mesmo objeto. |
| CA2007 | [CA2007: não aguardar diretamente uma tarefa](ca2007.md) | Um método assíncrono [aguarda](/dotnet/csharp/language-reference/keywords/await) um <xref:System.Threading.Tasks.Task> diretamente. Quando um método assíncrono aguarda uma <xref:System.Threading.Tasks.Task> continuação direta, ocorre no mesmo thread que criou a tarefa. Esse comportamento pode ser dispendioso em termos de desempenho e pode resultar em um deadlock no thread da interface do usuário. Considere chamar <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> para sinalizar sua intenção para continuação. |
| CA2008 | [CA2008: Não criar tarefas sem passar um TaskScheduler](ca2008.md) | Uma operação de criação ou de continuação de tarefa usa uma sobrecarga de método que não especifica um <xref:System.Threading.Tasks.TaskScheduler> parâmetro. |
| CA2009 | [CA2009: Não chamar ToImmutableCollection em um valor ImmutableCollection](ca2009.md) | `ToImmutable` o método não era necessariamente chamado em uma coleção imutável do <xref:System.Collections.Immutable> namespace. |
| CA2011 | [CA2011: Não atribuir a propriedade em seu próprio setter](ca2011.md) | Uma propriedade recebeu acidentalmente um valor dentro de seu próprio [acessador set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| CA2012 | [CA2012: Usar ValueTasks corretamente](ca2012.md) | ValueTasks retornados de invocações de membro devem ser diretamente aguardados.  Tenta consumir um ValueTask várias vezes ou para acessar diretamente um resultado antes que seja conhecido a ser concluído pode resultar em uma exceção ou corrupção.  Ignorar essa ValueTask é provavelmente uma indicação de um bug funcional e pode prejudicar o desempenho. |
| CA2013 | [CA2013: Não usar ReferenceEquals com tipos de valor](ca2013.md) | Ao comparar valores usando <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , se objA e objB forem tipos de valor, eles estarão em caixa antes de serem passados para o <xref:System.Object.ReferenceEquals%2A> método. Isso significa que, mesmo que objA e objB representem a mesma instância de um tipo de valor, o método, no <xref:System.Object.ReferenceEquals%2A> entanto, retorna false. |
| CA2014 | [CA2014: não use stackalloc em loops.](ca2014.md) | O espaço de pilha alocado por um stackalloc é liberado apenas no final da invocação do método atual.  Usá-lo em um loop pode resultar em aumento de pilha não associado e condições de estouro de pilha eventual. |
| CA2015 | [CA2015: não definir finalizadores para tipos derivados de MemoryManager &lt; T&gt;](ca2015.md) | Adicionar um finalizador a um tipo derivado de <xref:System.Buffers.MemoryManager%601> pode permitir que a memória seja liberada enquanto ainda estiver em uso por um <xref:System.Span%601> . |
| CA2016 | [CA2016: Encaminhe o parâmetro CancellationToken para os métodos que recebem um](ca2016.md) | Encaminhe o `CancellationToken` parâmetro para os métodos que usam um para garantir que as notificações de cancelamento da operação sejam propagadas corretamente ou repassem `CancellationToken.None` explicitamente para indicar, de forma intencional, não a propagação do token. |
| CA2100 | [CA2100: Examinar consultas SQL em busca de vulnerabilidades de segurança](../code-quality/ca2100.md) | Um método define a propriedade System.Data.IDbCommand.CommandText usando uma cadeia de caracteres criada com base em um argumento da cadeia de caracteres para o método. Esta regra pressupõe que o argumento da cadeia de caracteres contenha a entrada do usuário. Uma cadeia de caracteres de comando SQL criada com base na entrada do usuário é vulnerável a ataques de injeção SQL. |
| CA2101 |[CA2101: especificar o marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101.md) | Um membro de invocação da plataforma permite chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres e não realiza marshaling da cadeia de caracteres explicitamente. Isso pode causar uma vulnerabilidade de segurança em potencial. |
| CA2109 | [CA2109: Examinar manipuladores de eventos visíveis](../code-quality/ca2109.md) | Um método público ou protegido de tratamento de eventos foi detectado. Os métodos de tratamento de eventos não devem ser expostos, a menos que seja absolutamente necessário. |
| CA2119 | [CA2119: Selar métodos que atendem a interfaces particulares](../code-quality/ca2119.md) | Um tipo público herdável fornece uma implementação de método substituível de uma interface (Friend no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) interna. Para corrigir uma violação dessa regra, evite que o método seja substituído fora do assembly. |
| CA2153 |[CA2153: Evite lidar com exceções de estado corrompido](../code-quality/ca2153.md) | Exceções de estado corrompidas (CSEs) indicam que existe corrupção de memória em seu processo. A captura deles, em vez de permitir que o processo falhe, pode levar a vulnerabilidades de segurança se um invasor puder fazer uma exploração na região de memória corrompida. |
| CA2200 | [CA2200: Relançar para preservar detalhes da pilha](../code-quality/ca2200.md) | Uma exceção é lançada novamente e a exceção é especificada explicitamente na instrução throw. Se uma exceção for lançada novamente pela especificação da exceção na instrução throw, a lista de chamadas de método entre o método original que lançou a exceção e o método atual será perdida. |
| CA2201 | [CA2201: Não acionar tipos de exceção reservados](../code-quality/ca2201.md) | Isso torna o erro original difícil de detectar e depurar. |
| CA2207 | [CA2207: Inicializar campos estáticos de tipo de valor em linha](../code-quality/ca2207.md) | Um tipo de valor declara um construtor estático explícito. Para corrigir uma violação dessa regra, inicialize todos os dados estáticos quando declarados e remova o construtor estático. |
| CA2208 |[CA2208: Criar instância de exceções de argumento corretamente](../code-quality/ca2208.md) | For feita uma chamada para o construtor padrão (sem parâmetros) de um tipo de exceção que seja ou derive de ArgumentException, ou um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção que seja ou derive de ArgumentException. |
| CA2211 |[CA2211: Campos não constantes não devem ser visíveis](../code-quality/ca2211.md) | Os campos estáticos que não são constantes nem somente leitura não são thread-safe. O acesso a esse campo deve ser controlado cuidadosamente e exige técnicas de programação avançadas para sincronizar o acesso ao objeto da classe. |
| CA2213 | [CA2213: Campos descartáveis devem ser descartados](../code-quality/ca2213.md) | Um tipo que implementa System.IDisposable declara campos que são de tipos que também implementam IDisposable. O método Dispose do campo não é chamado pelo método Dispose do tipo declarante. |
| CA2214 | [CA2214: Não chamar métodos substituíveis em construtores](../code-quality/ca2214.md) | Ao chamar um método virtual, o construtor da instância que invoca o método pode não ter sido executado. |
| CA2215 | [CA2215: Métodos Dispose devem chamar o descarte da classe base](../code-quality/ca2215.md) | Se for herdado de um tipo descartável, um tipo deverá chamar o método Dispose do tipo de base em seu próprio método Dispose. |
| CA2216 |[CA2216: Tipos descartáveis devem declarar o finalizador](../code-quality/ca2216.md) | Um tipo que implementa System.IDisposable e tem campos que sugerem o uso de recursos não gerenciados não implementa um finalizador, conforme descrito por Object.Finalize. |
| CA2217 | [CA2217: Não marcar enumerações com FlagsAttribute](../code-quality/ca2217.md) |Uma enumeração visível externamente é marcada usando-se FlagsAttribute e tem um ou mais valores que não são potências de dois ou uma combinação dos outros valores definidos na enumeração. |
| CA2219 | [CA2219: Não acionar exceções em cláusulas de exceção](../code-quality/ca2219.md) | Quando uma exceção é acionada em uma cláusula finally ou fault, a nova exceção oculta a exceção ativa. Quando uma exceção é acionada em uma cláusula de filtro, o tempo de execução captura silenciosamente a exceção. Isso torna o erro original difícil de detectar e depurar. |
| CA2225 | [CA2225: Sobrecargas de operador têm alternativas nomeadas](../code-quality/ca2225.md) |Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado. O membro alternativo nomeado fornece acesso à mesma funcionalidade que o operador, e é fornecido para desenvolvedores que programem em linguagens que não dão suporte a operadores sobrecarregados. |
| CA2226 | [CA2226: Operadores devem ter sobrecargas simétricas](../code-quality/ca2226.md) | Um tipo implementa o operador de igualdade ou de desigualdade e não implementa o operador oposto. |
| CA2227 |[CA2227: Propriedades de coleção devem ser somente leitura](../code-quality/ca2227.md) |Uma propriedade collection gravável permite que um usuário substitua a coleção por uma coleção diferente. Uma propriedade somente leitura evita que a coleção seja substituída, mas ainda permite que membros individuais sejam definidos. |
| CA2229 | [CA2229: Implementar construtores de serialização](../code-quality/ca2229.md) | Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido. |
| CA2231 | [CA2231: Sobrecarregar operador equals ao substituir ValueType.Equals](../code-quality/ca2231.md) | Um tipo de valor substitui Object.Equals, mas não implementa o operador de igualdade. |
| CA2234 | [CA2234: Passar objetos System.Uri em vez de cadeias de caracteres](../code-quality/ca2234.md) | Foi feita uma chamada para um método com um parâmetro de cadeia de caracteres cujo nome contém "uri", "URI", "urn", "URN", "url" ou "URL". O tipo declarante do método contém uma sobrecarga do método correspondente que possui um parâmetro System.Uri. |
| CA2235 | [CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235.md) | Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável. |
| CA2237 | [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237.md) | Para serem reconhecidos pelo Common Language Runtime como serializáveis, os tipos devem ser marcados usando-se o atributo SerializableAttribute, mesmo quando o tipo usa uma rotina de serialização personalizada por meio da implementação da interface ISerializable. |
| CA2241 | [CA2241: Fornecer argumentos corretos para métodos de formatação](../code-quality/ca2241.md) | O argumento format passado para System.String.Format não contém um item de formato correspondente a cada argumento do objeto ou vice-versa. |
| CA2242 |[CA2242: Testar para NaN corretamente](../code-quality/ca2242.md) | Essa expressão testa um valor em Single.Nan ou Double.Nan. Use Single.IsNan (único) ou Double.IsNan (duplo) para testar o valor. |
| CA2243 |[CA2243: Literais de cadeias de caracteres de atributo devem ser analisados corretamente](../code-quality/ca2243.md) | O parâmetro literal da cadeia de caracteres de um atributo não é analisado corretamente para uma URL, um GUID ou uma versão. |
| CA2244 | [CA2244: Não duplicar inicializações de elementos indexados](../code-quality/ca2244.md) | Um inicializador de objeto tem mais de um inicializador de elemento indexado com o mesmo índice de constante. Todos, exceto o último inicializador, são redundantes. |
| CA2245 | [CA2245: Não atribuir uma propriedade a si mesma](../code-quality/ca2245.md) | Uma propriedade foi acidentalmente atribuída a ela mesma. |
| CA2246 | [CA2246: Não designar um símbolo e o membro dele na mesma instrução](../code-quality/ca2246.md) | Não é recomendável atribuir um símbolo e seu membro, ou seja, um campo ou uma propriedade, na mesma instrução. Não fica claro se o acesso de membro foi projetado para usar o valor antigo do símbolo antes da atribuição ou o novo valor da atribuição nesta instrução. |
| CA2247 | [CA2247: o argumento passado para o Construtor TaskCompletionSource deve ser TaskCreationOptions enum em vez de TaskContinuationOptions enum.](../code-quality/ca2247.md) | TaskCompletionSource tem construtores que usam TaskCreationOptions que controlam a tarefa subjacente e construtores que assumem o estado do objeto armazenado na tarefa.  Passar acidentalmente um TaskContinuationOptions em vez de um TaskCreationOptions resultará na chamada que trata as opções como estado. |
| CA2248 | [CA2248: Fornecer o argumento de enumeração correto para Enum.HasFlag](../code-quality/ca2248.md) | O tipo de enumeração passado como um argumento para a `HasFlag` chamada do método é diferente do tipo de enumeração de chamada. |
| CA2249 | [CA2249: Considerar o uso de String.Contains em vez de String.IndexOf](../code-quality/ca2249.md) | Chamadas para `string.IndexOf` onde o resultado é usado para verificar a presença/ausência de uma subcadeia de caracteres podem ser substituídas por `string.Contains` . |
| CA2300 | [CA2300: Não usar o desserializador BinaryFormatter não seguro](../code-quality/ca2300.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2301 | [CA2301: Não chamar BinaryFormatter.Deserialize sem antes definir BinaryFormatter.Binder](../code-quality/ca2301.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2302 | [CA2302: Verificar se o BinaryFormatter.Binder está definido antes de chamar BinaryFormatter.Deserialize](../code-quality/ca2302.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2305 | [CA2305: Não usar o desserializador inseguro LosFormatter](../code-quality/ca2305.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2310 | [CA2310: Não usar o desserializador inseguro NetDataContractSerializer](../code-quality/ca2310.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2311 | [CA2311: Não desserializar sem definir primeiro NetDataContractSerializer.Binder](../code-quality/ca2311.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2312 | [CA2312: Verificar se NetDataContractSerializer.Binder foi definido antes de desserializar](../code-quality/ca2312.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2315 | [CA2315: Não usar o desserializador inseguro ObjectStateFormatter](../code-quality/ca2315.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2321 | [CA2321: Não desserializar com JavaScriptSerializer usando um SimpleTypeResolver](../code-quality/ca2321.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2322 | [CA2322: Garantir que o JavaScriptSerializer não seja inicializado com SimpleTypeResolver antes de desserializar](../code-quality/ca2322.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2326 | [CA2326: Não usar valores de TypeNameHandling diferentes de None](../code-quality/ca2326.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2327 | [CA2327: Não usar JsonSerializerSettings não seguras](../code-quality/ca2327.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2328 | [CA2328: Verificar se as JsonSerializerSettings são seguras](../code-quality/ca2328.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2329 | [CA2329: Não desserializar com JsonSerializer usando uma configuração não segura](../code-quality/ca2329.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2330 | [CA2330: Verificar se o JsonSerializer tem uma configuração segura durante a desserialização](../code-quality/ca2330.md) | Desserializadores inseguros são vulneráveis ao desserializar dados não confiáveis. Um invasor pode modificar os dados serializados para incluir tipos inesperados para injetar objetos com efeitos colaterais mal-intencionados. |
| CA2350 | [CA2350: verifique se a entrada do DataTable.ReadXml() é confiável](ca2350.md) | Ao desserializar um <xref:System.Data.DataTable> com uma entrada não confiável, um invasor pode criar uma entrada mal-intencionada para executar um ataque de negação de serviço. Pode haver vulnerabilidades de execução remota de código desconhecido. |
| CA2351 | [CA2351: verifique se a entrada do DataSet.ReadXml() é confiável](ca2351.md) | Ao desserializar um <xref:System.Data.DataSet> com uma entrada não confiável, um invasor pode criar uma entrada mal-intencionada para executar um ataque de negação de serviço. Pode haver vulnerabilidades de execução remota de código desconhecido. |
| CA2352 | [CA2352: DataSet ou DataTable não seguros no tipo serializável podem ser vulneráveis a ataques de execução de código remoto](ca2352.md) | Uma classe ou estrutura marcada com <xref:System.SerializableAttribute> contém um <xref:System.Data.DataSet> <xref:System.Data.DataTable> campo ou propriedade, e não tem um <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353: DataSet ou DataTable não seguros no tipo serializável](ca2353.md) | Uma classe ou struct marcada com um atributo de serialização XML ou um atributo de contrato de dados contém um <xref:System.Data.DataSet> <xref:System.Data.DataTable> campo ou propriedade. |
| CA2354 | [CA2354: DataSet ou DataTable não seguros no grafo de objetos desserializados podem ser vulneráveis a ataques de execução de código remoto](ca2354.md) | A desserialização com uma <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> serializada e o grafo de objeto do tipo convertido podem incluir um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: DataSet ou DataTable não seguros no grafo de objetos desserializados](ca2355.md) | Desserializando quando o grafo de objeto do tipo convertido ou especificado pode incluir um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> . |
| CA2356 | [CA2356: DataSet não seguro ou DataTable no grafo de objeto desserializado da Web](ca2356.md) | Um método com um <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> ou <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> tem um parâmetro que pode fazer referência a um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: verifique se a classe gerada automaticamente que contém DataSet.ReadXml() não é usada quando os dados não são confiáveis](ca2361.md) | Ao desserializar um <xref:System.Data.DataSet> com uma entrada não confiável, um invasor pode criar uma entrada mal-intencionada para executar um ataque de negação de serviço. Pode haver vulnerabilidades de execução remota de código desconhecido. |
| CA2362 | [CA2362: DataSet ou DataTable não seguros em um tipo serializável gerado automaticamente podem ser vulneráveis a ataques de execução remota de código](ca2362.md) | Ao desserializar a entrada não confiável com <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> o e o grafo de objeto desserializado contiver um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> , um invasor poderá criar uma carga mal-intencionada para executar um ataque de execução remota de código. |
| CA3001 | [CA3001: Examinar código quanto a vulnerabilidades de injeção de SQL](../code-quality/ca3001.md) | Ao trabalhar com comandos de entrada e SQL não confiáveis, lembre-se dos ataques de injeção de SQL. Um ataque de injeção de SQL pode executar comandos SQL mal-intencionados, comprometendo a segurança e a integridade do seu aplicativo. |
| CA3002 | [CA3002: Examinar código quanto a vulnerabilidades de XSS](../code-quality/ca3002.md) | Ao trabalhar com entrada não confiável de solicitações da Web, tenha cuidado com ataques XSS (scripts entre sites). Um ataque XSS injeta entrada não confiável em saída HTML bruta, permitindo que o invasor execute scripts mal-intencionados ou modifique conteúdo de forma mal-intencionada em sua página da Web. |
| CA3003 | [CA3003: Examinar código quanto a vulnerabilidades de injeção de caminho](../code-quality/ca3003.md) | Ao trabalhar com entrada não confiável de solicitações da Web, lembre-se de usar a entrada controlada pelo usuário ao especificar caminhos para arquivos. |
| CA3004 | [CA3004: Examinar código quanto a vulnerabilidades de divulgação de informações](../code-quality/ca3004.md) | A divulgação de informações de exceção dá aos invasores insights sobre os internos do seu aplicativo, o que pode ajudar os invasores a encontrar outras vulnerabilidades a serem exploradas. |
| CA3006 | [CA3006: Examinar código quanto a vulnerabilidades de injeção de comando de processo](../code-quality/ca3006.md) | Ao trabalhar com entrada não confiável, lembre-se dos ataques de injeção de comando. Um ataque de injeção de comando pode executar comandos mal-intencionados no sistema operacional subjacente, comprometendo a segurança e a integridade do servidor. |
| CA3007 | [CA3007: Examinar código quanto a vulnerabilidades de redirecionamento aberto](../code-quality/ca3007.md) | Ao trabalhar com entrada não confiável, lembre-se de vulnerabilidades de redirecionamento abertas. Um invasor pode explorar uma vulnerabilidade de redirecionamento aberto para usar seu site para dar a aparência de uma URL legítima, mas redirecionar um visitante dessuspeito para um phishing ou outra página da Web mal-intencionada. |
| CA3008 | [CA3008: Examinar código quanto a vulnerabilidades de injeção de XPath](../code-quality/ca3008.md) | Ao trabalhar com entrada não confiável, lembre-se de ataques de injeção de XPath. A construção de consultas XPath usando a entrada não confiável pode permitir que um invasor manipule a consulta de forma mal-intencionada para retornar um resultado indesejado e possivelmente divulgar o conteúdo do XML consultado. |
| CA3009 | [CA3009: Examinar código quanto a vulnerabilidades de injeção de XML](../code-quality/ca3009.md) | Ao trabalhar com entrada não confiável, lembre-se de ataques de injeção de XML. |
| CA3010 | [CA3010: Examinar código quanto a vulnerabilidades de injeção de XAML](../code-quality/ca3010.md) | Ao trabalhar com entrada não confiável, lembre-se dos ataques de injeção XAML. XAML é uma linguagem de marcação que representa diretamente a instanciação e execução de objetos. Isso significa que os elementos criados em XAML podem interagir com recursos do sistema (por exemplo, acesso à rede e e/s do sistema de arquivos). |
| CA3011 | [CA3011: Examinar código quanto a vulnerabilidades de injeção de DLL](../code-quality/ca3011.md) | Ao trabalhar com uma entrada não confiável, lembre-se de carregar código não confiável. Se o seu aplicativo Web carregar código não confiável, um invasor poderá injetar DLLs mal-intencionadas em seu processo e executar código mal-intencionado. |
| CA3012 | [CA3012: Examinar código quanto a vulnerabilidades de injeção de regex](../code-quality/ca3012.md) | Ao trabalhar com entrada não confiável, lembre-se dos ataques de injeção de Regex. Um invasor pode usar a injeção de Regex para modificar uma expressão regular de forma mal-intencionada, para fazer com que o Regex coincida com resultados indesejados ou para fazer com que o Regex consuma CPU excessiva, resultando em um ataque de negação de serviço. |
| CA3061 | [CA3061: Não adicionar esquema por URL](../code-quality/ca3061.md) | Não use a sobrecarga não segura do método Add, pois isso pode causar referências externas perigosas. |
| CA3075 | [CA3075: Processamento de DTD não seguro](../code-quality/ca3075.md) | Se você usar instâncias DTDProcessing inseguras ou referenciar fontes externas de entidade, o analisador poderá aceitar entrada não confiável e divulgar informações confidenciais a invasores. |
| CA3076 | [CA3076: Execução de script XSLT não seguro](../code-quality/ca3076.md) | Se você executar a XSLT (Extensible Stylesheet Language Transformations) em aplicativos .NET de forma insegura, o processador poderá resolver referências de URI não confiáveis que poderiam divulgar informações confidenciais para invasores, levando à negação de serviço e a ataques entre sites. |
| CA3077 | [CA3077: Processamento não seguro no design de API, no documento XML e no leitor de texto XML](../code-quality/ca3077.md) | Ao criar uma API derivada de XMLDocument e XMLTextReader, lembre-se de DtdProcessing. Usar instâncias DTDProcessing inseguras ao referenciar ou resolver fontes de entidade externas ou definir valores inseguros no XML pode levar à divulgação de informações. |
| CA3147 | [CA3147: Marcar manipuladores de verbo com ValidateAntiForgeryToken](../code-quality/ca3147.md) | Ao criar um controlador MVC ASP.NET, lembre-se de ataques de solicitação entre sites forjado. Um ataque de falsificação de solicitação entre sites pode enviar solicitações mal-intencionadas de um usuário autenticado para o controlador MVC ASP.NET. |
| CA5350 | [CA5350: Não usar algoritmos de criptografia fracos](../code-quality/ca5350.md) | Algoritmos de criptografia fracos e funções de hash são usados hoje por vários motivos, mas eles não devem ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem. Essa regra é disparada quando encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|
| CA5351 | [CA5351 não use algoritmos de criptografia desfeitos](../code-quality/ca5351.md) | Os algoritmos de criptografia desfeitos não são considerados seguros e seu uso deve ser altamente desencorajado. Essa regra é disparada quando encontra o algoritmo de hash MD5 ou os algoritmos de criptografia DES ou RC2 no código. |
| CA5358 | [CA5358: Não usar modos de criptografia não seguros](../code-quality/ca5358.md) | Não usar modos de criptografia não seguros |
| CA5359 | [CA5359 não desabilitar a validação de certificado](../code-quality/ca5359.md) | Um certificado pode ajudar a autenticar a identidade do servidor. Os clientes devem validar o certificado do servidor para garantir que as solicitações sejam enviadas ao servidor pretendido. Se o ServerCertificateValidationCallback sempre retornar `true` , qualquer certificado passará na validação. |
| CA5360 | [CA5360 não chamar métodos perigosos na desserialização](../code-quality/ca5360.md) | A desserialização insegura é uma vulnerabilidade que ocorre quando dados não confiáveis são usados para proutilizar a lógica de um aplicativo, causarem um ataque de negação de serviço (DoS) ou até mesmo executar um código arbitrário quando ele estiver desserializado. Frequentemente, é possível que usuários mal-intencionados abusam esses recursos de desserialização quando o aplicativo estiver desserializando dados não confiáveis que estão sob seu controle. Especificamente, invoque métodos perigosos no processo de desserialização. Ataques de desserialização inseguros com êxito podem permitir que um invasor execute ataques, como ataques de DoS, desvios de autenticação e execução remota de código. |
| CA5361 | [CA5361: não desabilitar o uso do Schannel de criptografia forte](../code-quality/ca5361.md) | `Switch.System.Net.DontEnableSchUseStrongCrypto`A configuração para `true` enfraquece a criptografia usada em conexões TLS (segurança da camada de transporte) de saída. A criptografia mais fraca pode comprometer a confidencialidade da comunicação entre o aplicativo e o servidor, tornando mais fácil para os invasores bisbilhotarem dados confidenciais. |
| CA5362 | [Ciclo de referência potencial do CA5362 no grafo de objeto desserializado](../code-quality/ca5362.md) | Se estiver desserializando dados não confiáveis, qualquer código que processe o grafo de objeto desserializado precisará manipular os ciclos de referência sem entrar em loops infinitos. Isso inclui o código que faz parte de um retorno de chamada de desserialização e o código que processa o grafo de objeto após a desserialização ser concluída. Caso contrário, um invasor pode executar um ataque de negação de serviço com dados mal-intencionados que contenham um ciclo de referência. |
| CA5363 | [CA5363: Não desabilitar a validação de solicitação](../code-quality/ca5363.md) | A validação de solicitação é um recurso no ASP.NET que examina as solicitações HTTP e determina se elas contêm conteúdo potencialmente perigoso que pode levar a ataques de injeção, incluindo scripts entre sites. |
| CA5364 | [CA5364: Não use protocolos de segurança preteridos](../code-quality/ca5364.md) | A segurança de camada de transporte (TLS) protege a comunicação entre computadores, mais comumente com HTTPS (Hypertext Transfer Protocol Secure). Versões de protocolo mais antigas do TLS são menos seguras do que o TLS 1,2 e o TLS 1,3 e têm mais probabilidade de ter novas vulnerabilidades. Evite versões de protocolo mais antigas para minimizar o risco. |
| CA5365 | [CA5365 não desabilita a verificação de cabeçalho HTTP](../code-quality/ca5365.md) | A verificação de cabeçalho HTTP permite a codificação do retorno de carro e dos caracteres de nova linha, \r e \n, que são encontrados nos cabeçalhos de resposta. Essa codificação pode ajudar a evitar ataques de injeção que exploram um aplicativo que ecoa dados não confiáveis contidos no cabeçalho. |
| CA5366 | [CA5366 usar XmlReader para XML de leitura de DataSet](../code-quality/ca5366.md) | Usar um <xref:System.Data.DataSet> para ler XML com dados não confiáveis pode carregar referências externas perigosas, que devem ser restringidas usando um <xref:System.Xml.XmlReader> com um resolvedor seguro ou com o processamento de DTD desabilitado. |
| CA5367 | [CA5367 não serializam tipos com campos de ponteiro](../code-quality/ca5367.md) | Esta regra verifica se há uma classe serializável com um campo ou propriedade de ponteiro. Os membros que não podem ser serializados podem ser um ponteiro, como membros estáticos ou campos marcados com <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Set ViewStateUserKey para classes derivadas da página](../code-quality/ca5368.md) | Definir a <xref:System.Web.UI.Page.ViewStateUserKey> propriedade pode ajudá-lo a evitar ataques em seu aplicativo, permitindo que você atribua um identificador à variável de estado de exibição para usuários individuais para que os invasores não possam usar a variável para gerar um ataque. Caso contrário, haverá vulnerabilidades para falsificação de solicitação entre sites. |
| CA5369 | [CA5369: Usar o XmlReader para desserializar](../code-quality/ca5369.md) | O processamento de esquemas XML e DTD não confiáveis pode permitir o carregamento de referências externas perigosas, que devem ser restringidas com o uso de um XmlReader com um resolvedor seguro ou com o processamento de esquema embutido XML e DTD desabilitado. |
| CA5370 | [CA5370: Usar o XmlReader para validar o leitor](../code-quality/ca5370.md) | O processamento de esquemas XML e DTD não confiáveis pode permitir o carregamento de referências externas perigosas. Esse carregamento perigoso pode ser restringido usando um XmlReader com um resolvedor seguro ou com o processamento de esquema embutido XML e DTD desabilitado. |
| CA5371 | [CA5371: Usar o XmlReader para a leitura do esquema](../code-quality/ca5371.md) | O processamento de esquemas XML e DTD não confiáveis pode permitir o carregamento de referências externas perigosas. O uso de um XmlReader com um resolvedor seguro ou com o processamento de esquema embutido XML e DTD desabilitado restringe isso. |
| CA5372 | [CA5372: Usar o XmlReader para o XPathDocument](../code-quality/ca5372.md) | O processamento de XML de dados não confiáveis pode carregar referências externas perigosas, que podem ser restringidas usando um XmlReader com um resolvedor seguro ou com o processamento de DTD desabilitado. |
| CA5373 | [CA5373: Não usar a função de derivação de chave obsoleta](../code-quality/ca5373.md) | Essa regra detecta a invocação de métodos de derivação de chave fraca <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> e `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> usou um algoritmo fraco de PBKDF1. |
| CA5374 | [CA5374 não use XslTransform](../code-quality/ca5374.md) | Essa regra verifica se <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> é criada uma instância no código. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> Agora é obsoleto e não deve ser usado. |
| CA5375 | [CA5375 não usar assinatura de acesso compartilhado de conta](../code-quality/ca5375.md) | Uma SAS de conta pode delegar acesso a operações de leitura, gravação e exclusão em contêineres de BLOB, tabelas, filas e compartilhamentos de arquivos que não são permitidos com uma SAS de serviço. No entanto, ele não dá suporte a políticas em nível de contêiner e tem menos flexibilidade e controle sobre as permissões concedidas. Depois que os usuários mal-intencionados o obtiverem, sua conta de armazenamento será comprometida facilmente. |
| CA5376 | [CA5376 usar SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | SAS são dados confidenciais que não podem ser transportados em texto sem formatação em HTTP. |
| CA5377 | [CA5377 usar política de acesso no nível do contêiner](../code-quality/ca5377.md) | Uma política de acesso no nível de contêiner pode ser modificada ou revogada a qualquer momento. Ele fornece maior flexibilidade e controle sobre as permissões concedidas. |
| CA5378 | [CA5378: Não desabilite ServicePointManagerSecurityProtocols](../code-quality/ca5378.md) | Configuração `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` para `true` limita as conexões de TLS (segurança de camada de transporte) do Windows Communication Framework (WCF) usando o TLS 1,0. Essa versão do TLS será preterida. |
| CA5379 | [CA5379 não usa algoritmo de função de derivação de chave fraca](../code-quality/ca5379.md) | A <xref:System.Security.Cryptography.Rfc2898DeriveBytes> classe assume como padrão o uso do <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algoritmo. Você deve especificar o algoritmo de hash a ser usado em algumas sobrecargas do construtor com <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> ou superior. Observe <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> que Property tem apenas um `get` acessador e não tem um `overriden` modificador. |
| CA5380 | [CA5380: Não adicionar certificados ao repositório raiz](../code-quality/ca5380.md) | Essa regra detecta o código que adiciona um certificado ao repositório de certificados das autoridades de certificação raiz confiáveis. Por padrão, o repositório de certificados de autoridades de certificação raiz confiáveis é configurado com um conjunto de CAs públicas que atendem aos requisitos do programa de certificado raiz da Microsoft. |
| CA5381 | [CA5381: Verificar que os certificados não sejam adicionados ao repositório raiz](../code-quality/ca5381.md) | Essa regra detecta o código que potencialmente adiciona um certificado ao repositório de certificados de autoridades de certificação raiz confiáveis. Por padrão, o repositório de certificados de autoridades de certificação raiz confiáveis é configurado com um conjunto de CAs (autoridades de certificação) públicas que atendem aos requisitos do Microsoft Root Certificate Program. |
| CA5382 | [CA5382 usar cookies seguros no ASP.NET Core](../code-quality/ca5382.md) | Os aplicativos disponíveis via HTTPS devem usar cookies seguros, que indicam ao navegador que o cookie só deve ser transmitido usando protocolo SSL (SSL). |
| CA5383 | [CA5383 garantir o uso de cookies seguros no ASP.NET Core](../code-quality/ca5383.md) | Os aplicativos disponíveis via HTTPS devem usar cookies seguros, que indicam ao navegador que o cookie só deve ser transmitido usando protocolo SSL (SSL). |
| CA5384 | [CA5384 não usar o algoritmo de assinatura digital (DSA)](../code-quality/ca5384.md) | O DSA é um algoritmo de criptografia assimétrica fraco. |
| CA5385 | [CA5385 use o algoritmo Rivest – Shamir – Adleman (RSA) com tamanho de chave suficiente](../code-quality/ca5385.md) | Uma chave RSA inferior a 2048 bits é mais vulnerável a ataques de força bruta. |
| CA5386 | [CA5386: Evitar codificar o valor SecurityProtocolType](../code-quality/ca5386.md) | A segurança de camada de transporte (TLS) protege a comunicação entre computadores, mais comumente com HTTPS (Hypertext Transfer Protocol Secure). As versões de protocolo TLS 1,0 e TLS 1,1 foram preteridas, enquanto TLS 1,2 e TLS 1,3 são atuais. No futuro, o TLS 1,2 e o TLS 1,3 podem ser preteridos. Para garantir que seu aplicativo permaneça seguro, evite codificar uma versão de protocolo e ter como destino pelo menos .NET Framework v 4.7.1. |
| CA5387 | [CA5387 não usa função de derivação de chave fraca com contagem de iteração insuficiente](../code-quality/ca5387.md) | Esta regra verifica se uma chave criptográfica foi gerada por <xref:System.Security.Cryptography.Rfc2898DeriveBytes> com uma contagem de iteração inferior a 100.000. Uma contagem de iteração mais alta pode ajudar a mitigar contra ataques de dicionário que tentam adivinhar a chave de criptografia gerada. |
| CA5388 | [CA5388 garantir contagem de iteração suficiente ao usar a função de derivação de chave fraca](../code-quality/ca5388.md) | Esta regra verifica se uma chave de criptografia foi gerada pelo <xref:System.Security.Cryptography.Rfc2898DeriveBytes> com uma contagem de iteração que pode ser menor que 100.000. Uma contagem de iteração mais alta pode ajudar a mitigar contra ataques de dicionário que tentam adivinhar a chave de criptografia gerada. |
| CA5389 | [CA5389: Não adicionar o caminho do item de arquivo ao caminho do sistema de arquivos de destino](../code-quality/ca5389.md) | O caminho do arquivo pode ser relativo e pode levar ao acesso do sistema de arquivos fora do caminho de destino do sistema de arquivos esperado, levando a alterações de configuração mal-intencionadas e à execução remota de código por meio da técnica de Lay-and-wait. |
| CA5390 | [CA5390 não embutir código chave de criptografia](../code-quality/ca5390.md) | Para que um algoritmo simétrico seja bem-sucedido, a chave secreta deve ser conhecida somente pelo remetente e pelo destinatário. Quando uma chave é embutida em código, ela é facilmente descoberta. Mesmo com binários compilados, é fácil para usuários mal-intencionados extraí-lo. Depois que a chave privada for comprometida, o texto cifrado poderá ser descriptografado diretamente e não será mais protegido. |
| CA5391 | [CA5391 usar tokens antifalsificação em controladores MVC ASP.NET Core](../code-quality/ca5391.md) | Manipular uma `POST` `PUT` solicitação,, `PATCH` ou `DELETE` sem validar um token de antifalsificação pode estar vulnerável a ataques de solicitação entre sites forjada. Um ataque de falsificação de solicitação entre sites pode enviar solicitações mal-intencionadas de um usuário autenticado para seu controlador ASP.NET Core MVC. |
| CA5392 | [CA5392 usar o atributo DefaultDllImportSearchPaths para P/Invokes](../code-quality/ca5392.md) | Por padrão, as funções P/Invoke usam a <xref:System.Runtime.InteropServices.DllImportAttribute> investigação de um número de diretórios, incluindo o diretório de trabalho atual para a biblioteca carregar. Isso pode ser um problema de segurança para determinados aplicativos, levando ao seqüestro de DLL. |
| CA5393 | [CA5393 não usa valor DllImportSearchPath não seguro](../code-quality/ca5393.md) | Pode haver uma DLL mal-intencionada nos diretórios de pesquisa padrão de DLL e no assembly. Ou, dependendo de onde o aplicativo é executado, pode haver uma DLL mal-intencionada no diretório do aplicativo. |
| CA5394 | [CA5394 não usam randomização insegura](../code-quality/ca5394.md) | O uso de um gerador de números pseudo aleatórios criptograficamente fraco pode permitir que um invasor preveja qual valor de segurança será gerado. |
| CA5395 | [Atributo CA5395 ausente HttpVerb para métodos de ação](../code-quality/ca5395.md) | Todos os métodos de ação que criam, editam, excluem ou modificam os dados precisam ser protegidos com o atributo antifalsificação de ataques de falsificação de solicitação entre sites. A execução de uma operação GET deve ser uma operação segura que não tenha efeitos colaterais e não modifique seus dados persistentes. |
| CA5396 | [CA5396 definir HttpOnly como true para HttpCookie](../code-quality/ca5396.md) | Como uma medida de defesa profunda, verifique se os cookies HTTP sensíveis à segurança estão marcados como HttpOnly. Isso indica que os navegadores da Web devem impedir que os scripts acessem os cookies. Scripts maliciosos injetados são uma maneira comum de roubar cookies. |
| CA5397 | [CA5397: Não usar valores de SslProtocols preteridos](../code-quality/ca5397.md) | A segurança de camada de transporte (TLS) protege a comunicação entre computadores, mais comumente com HTTPS (Hypertext Transfer Protocol Secure). Versões de protocolo mais antigas do TLS são menos seguras do que o TLS 1,2 e o TLS 1,3 e têm mais probabilidade de ter novas vulnerabilidades. Evite versões de protocolo mais antigas para minimizar o risco. |
| CA5398 | [CA5398: Evitar valores de SslProtocols fixos](../code-quality/ca5398.md) | A segurança de camada de transporte (TLS) protege a comunicação entre computadores, mais comumente com HTTPS (Hypertext Transfer Protocol Secure). As versões de protocolo TLS 1,0 e TLS 1,1 foram preteridas, enquanto TLS 1,2 e TLS 1,3 são atuais. No futuro, o TLS 1,2 e o TLS 1,3 podem ser preteridos. Para garantir que seu aplicativo permaneça seguro, evite codificar uma versão de protocolo. |
| CA5399 | [CA5399 definitivamente desabilitar a verificação da lista de certificados revogados do HttpClient](../code-quality/ca5399.md) | Um certificado revogado não é mais confiável. Ele pode ser usado por invasores passando dados mal-intencionados ou roubando dados confidenciais na comunicação HTTPS. |
| CA5400 | [CA5400 garantir que a verificação da lista de certificados revogados do HttpClient não esteja desabilitada](../code-quality/ca5400.md) | Um certificado revogado não é mais confiável. Ele pode ser usado por invasores passando dados mal-intencionados ou roubando dados confidenciais na comunicação HTTPS. |
| CA5401 | [CA5401 não use createencryptr com IV não padrão](../code-quality/ca5401.md) | A criptografia simétrica sempre deve usar um vetor de inicialização não reproduzível para evitar ataques de dicionário. |
| CA5402 | [CA5402 usar createencryptr com o IV padrão](../code-quality/ca5402.md) | A criptografia simétrica sempre deve usar um vetor de inicialização não reproduzível para evitar ataques de dicionário. |
| CA5403 | [CA5403: Não embutir o certificado em código](../code-quality/ca5403.md) | O `data` `rawData` parâmetro ou de um <xref:System.Security.Cryptography.X509Certificates.X509Certificate> Construtor ou é embutido <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> em código. |
| IL3000 | [IL3000 Evite acessar o caminho do arquivo de assembly ao publicar como um único arquivo](../code-quality/il3000.md) | Evite usar o caminho do arquivo de assembly de acesso ao publicar como um único arquivo |
| IL3001 | [IL3001 Evite acessar o caminho do arquivo de assembly ao publicar como um arquivo único](../code-quality/il3001.md) | Evite acessar o caminho do arquivo de assembly ao publicar como um arquivo único |
