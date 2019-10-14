---
title: Avisos da análise de código para código gerenciado por CheckId
ms.date: 04/18/2019
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1068
- CA1200
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
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
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6ac6fccb69770c003f21875e5ab3809c2d6415b4
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305873"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Avisos da análise de código para código gerenciado por CheckId

A tabela a seguir lista avisos de análise de código para código gerenciado pelo identificador CheckId do aviso.

| CheckId | Aviso | Descrição |
|---------| - | - |
| CA1000 | [CA1000: Não declare membros estáticos em tipos genéricos @ no__t-0 | Quando um membro estático de um tipo genérico é chamado, o argumento de tipo deve ser especificado para o tipo. Quando um membro de instância genérico que não dá suporte à inferência é chamado, o argumento de tipo deve ser especificado para o membro. Nesses dois casos, a sintaxe para especificar o argumento de tipo é diferente e facilmente confundida. |
| CA1001 | [CA1001: os tipos com campos descartáveis devem ser descartáveis](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Uma classe declara e implementa um campo de instância que é um tipo System.IDisposable, e a classe não implementa IDisposable. Uma classe que declara um campo IDisposable indiretamente possui um recurso não gerenciado e deve implementar a interface IDisposable. |
| CA1002 | [CA1002: Não exponha listas genéricas @ no__t-0 | Generic < (de \<(T >) >) é uma coleção genérica que foi projetada para desempenho, não a herança. Por isso, List não contém membros virtuais. As coleções genéricas projetadas para herança devem ser expostas em seu lugar. |
| CA1003 | [CA1003: Usar instâncias de manipulador de eventos genéricas @ no__t-0 |Um tipo contém um delegado que retorna void, cuja assinatura contém dois parâmetros (o primeiro um objeto e o segundo um tipo atribuível a EventArgs), e o assembly que contém tem como alvo o Microsoft .NET Framework 2.0. |
| CA1004 | [CA1004: Os métodos genéricos devem fornecer o parâmetro de tipo @ no__t-0 | Inferência é como o argumento de tipo de um método genérico é determinado pelo tipo de argumento passado para o método, em vez da especificação explícita do argumento de tipo. Para habilitar a inferência, a assinatura do parâmetro de um método genérico deve incluir um parâmetro que seja do mesmo tipo do parâmetro de tipo para o método. Nesse caso, o argumento de tipo não precisa ser especificado. Durante o uso da inferência para todos os parâmetros de tipo, a sintaxe para chamar métodos de instância genéricos e não genéricos é idêntica; isso simplifica a usabilidade de métodos genéricos. |
| CA1005 | [CA1005: Evite parâmetros excessivos em tipos genéricos @ no__t-0 | Quanto mais parâmetros de tipo um tipo genérico contiver, mais difícil será saber e lembrar-se do que cada parâmetro de tipo representa. É normalmente óbvio com um parâmetro de tipo, como na lista\<T > e, em certos casos que têm dois parâmetros de tipo, como em Dictionary\<TKey, TValue >. No entanto, se houver mais de dois parâmetros de tipo, a dificuldade ficará muito grande para a maioria dos usuários. |
| CA1006 | [CA1006: Não aninhe tipos genéricos em assinaturas de membro @ no__t-0 | Um argumento de tipo aninhado é um argumento de tipo que também é um tipo genérico. Para chamar um membro cuja assinatura contenha um argumento de tipo aninhado, o usuário deve criar uma instância de um tipo genérico e passar esse tipo para o construtor de um segundo tipo genérico. O procedimento e a sintaxe obrigatórios são complexos e devem ser evitados. |
| CA1007 |[CA1007: Usar genéricos onde @ no__t-0 apropriado | Um método visível externamente contém um parâmetro de referência do tipo System.Object. O uso de um método genérico permite que todos os tipos, sujeitos a restrições, sejam passados para o método sem primeiramente converter o tipo no tipo de parâmetro de referência. |
| CA1008 | [CA1008: Enums devem ter valor zero @ no__t-0 | O valor padrão de uma enumeração não inicializada, assim como o de outros tipos de valor, é zero. Uma enumeração atribuída por nonflags deve definir um membro usando o valor de zero de forma que o valor padrão seja um valor válido da enumeração. Se uma enumeração que tem o atributo FlagsAttribute aplicado definir um membro com valor, seu nome deverá ser “None” para indicar que nenhum valor foi definido na enumeração. |
| CA1009 | [CA1009: Declarar manipuladores de eventos corretamente @ no__t-0 | Os métodos de manipulador de eventos utilizam dois parâmetros. O primeiro é do tipo System.Object e é chamado de "sender". Este é o objeto que acionou o evento. O segundo parâmetro é do tipo System.EventArgs e é chamado de "e". Esses são os dados associados ao evento. Os métodos do manipulador de eventos não devem retornar um valor; na linguagem de programação C#, isso é indicado pelo tipo de retorno nulo. |
| CA1010 | [CA1010: As coleções devem implementar a interface genérica @ no__t-0 | Para ampliar a usabilidade de uma coleção, implemente uma das interfaces da coleção genéricas. Em seguida, a coleção pode ser usada para popular tipos de coleção genéricos. |
| CA1011 |[CA1011: Considere passar tipos base como parâmetros @ no__t-0 | Quando um tipo de base é especificado como um parâmetro em uma declaração de método, qualquer tipo derivado do tipo de base pode ser passado como o argumento correspondente ao método. Se a funcionalidade adicional fornecida pelo tipo de parâmetro derivado não for necessária, o uso do tipo de base permitirá um uso mais amplo do método. |
| CA1012 | [CA1012: Tipos abstratos não devem ter construtores @ no__t-0 | Construtores em tipos abstratos só podem ser chamados por tipos derivados. Como construtores públicos criam instâncias de um tipo e não é possível criar instâncias de um tipo abstrato, um tipo abstrato com um construtor público é projetado incorretamente. |
| CA1013 | [CA1013: Sobrecarga do operador Equals ao sobrecarregar adicionar e subtrair @ no__t-0 | Um tipo público ou protegido implementa os operadores de adição ou subtração sem implementar o operador de igualdade. |
| CA1014 | [CA1014: Marcar assemblies com CLSCompliantAttribute @ no__t-0 | A CLS (Common Language Specification) define restrições de nomenclatura, tipos de dados e regras que assemblies deverão respeitar se forem usados em todas as linguagens de programação. Um bom design determina que todos os assemblies indiquem explicitamente a conformidade com CLS usando-se <xref:System.CLSCompliantAttribute>. Se esse atributo não estiver presente em um assembly, o assembly não será compatível. |
| CA1016 | [CA1016: Marcar assemblies com AssemblyVersionAttribute @ no__t-0 | O .NET usa o número de versão para identificar exclusivamente um assembly e associar a tipos em assemblies com nomes de alta segurança. O número de versão é usado com a versão e a política do publicador. Por padrão, os aplicativos só são executados com a versão do assembly com que foram criados. |
| CA1017 | [CA1017: Marcar assemblies com ComVisibleAttribute @ no__t-0 |ComVisibleAttribute determina como clientes COM acessam código gerenciado. Um bom design determina que os assemblies indiquem explicitamente a visibilidade de COM. A visibilidade de COM pode ser definida para todo o assembly e, em seguida, substituída por tipos individuais e membros de tipo. Caso esse atributo não esteja presente, o conteúdo do assembly permanece visível aos clientes COM. |
| CA1018 | [CA1018: Marcar atributos com AttributeUsageAttribute @ no__t-0 | Ao definir um atributo personalizado, você o marca usando AttributeUsageAttribute para indicar onde o atributo personalizado pode ser aplicado no código-fonte. O significado e o uso desejado de um atributo determinarão seus locais válidos no código. |
| CA1019 | [CA1019: Definir acessadores para argumentos de atributo @ no__t-0 | Os atributos podem definir argumentos obrigatórios que devem ser especificados quando você aplica o atributo a um destino. Eles também são conhecidos como argumentos posicionais porque são fornecidos a construtores de atributos como parâmetros posicionais. Para cada argumento obrigatório, o atributo também deve fornecer uma propriedade somente leitura correspondente de forma que o valor do argumento possa ser recuperado no tempo de execução. Os atributos também podem definir argumentos opcionais, que também são conhecidos como argumentos nomeados. Esses argumentos são fornecidos a construtores de atributo por nome e devem ter uma propriedade de leitura/gravação correspondente. |
| CA1020 | [CA1020: Evite namespaces com poucos tipos @ no__t-0 | Verifique se cada um dos namespaces tem uma organização lógica e se há um motivo válido para colocar tipos em um namespace populado de maneira esparsa. |
| CA1021 | [CA1021: Evite parâmetros de saída @ no__t-0 | A passagem de tipos por referência (usando out ou ref) requer experiência com ponteiros, compreensão das diferenças entre tipos de valor e tipos de referência e os métodos de tratamento com vários valores de retorno. Além disso, a diferença entre parâmetros out e ref não é amplamente compreendida. |
| CA1023 | [CA1023: Os indexadores não devem ser multidimensional @ no__t-0 | Os indicadores (ou seja, propriedades indexadas) devem usar um único índice. Os indicadores multidimensionais podem reduzir significativamente a usabilidade da biblioteca. |
| CA1024 | [CA1024: Use as propriedades onde @ no__t-0 apropriado | Um método público ou protegido tem um nome que começa com "Get", não utiliza parâmetros e retorna um valor que não é uma matriz. O método pode ser um bom candidato a se tornar uma propriedade. |
| CA1025 | [CA1025: Substituir argumentos repetitivos pela matriz params @ no__t-0 | Use uma matriz de parâmetros, em vez de argumentos repetidos, quando o número exato de argumentos for desconhecido e quando os argumentos variáveis forem do mesmo tipo ou puderem ser passados como o mesmo tipo. |
| CA1026 | [CA1026: Os parâmetros padrão não devem ser usados @ no__t-0 | Métodos que usam parâmetros padrão são permitidos na CLS; no entanto, a CLS permite que os compiladores ignorem os valores que são atribuídos a esses parâmetros. Para manter o comportamento desejado em todas as linguagens de programação, os métodos que usam parâmetros padrão devem ser substituídos por sobrecargas de método que forneçam os parâmetros padrão. |
| CA1027 |[CA1027: Marcar enums com FlagsAttribute @ no__t-0 | Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Aplique FlagsAttribute a uma enumeração quando suas constantes nomeadas puderem ser combinadas de maneira significativa. |
| CA1028 | [CA1028: O armazenamento de enumeração deve ser Int32 @ no__t-0 | Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Por padrão, o tipo de dados System.Int32 é usado para armazenar o valor constante. Embora seja possível alterar esse tipo subjacente, isso não é necessário ou recomendado na maioria dos cenários. |
| CA1030 | [CA1030: Usar eventos quando @ no__t-0 apropriado |Essa regra detecta métodos que têm nomes que seriam usados normalmente em eventos. Se um método for chamado em resposta a uma alteração de estado claramente definida, o método deverá ser invocado por um manipulador de eventos. Os objetos que chamam o método devem acionar eventos, em vez de chamar o método diretamente. |
| CA1031 | [CA1031: Não capturar tipos de exceção geral @ no__t-0 | As exceções gerais não devem ser capturadas. Capture uma exceção mais específica ou relance a exceção geral como a última instrução no bloco de captura. |
| CA1032 |[CA1032: Implementar construtores de exceção padrão @ no__t-0 | Deixar de fornecer o conjunto completo de construtores pode dificultar o tratamento correto das exceções. |
| CA1033 | [CA1033: Métodos de interface devem ser chamados por tipos filho @ no__t-0 | Um tipo visível externamente sem lacre fornece uma implementação de método explícita de uma interface pública e não fornece um método visível externamente alternativo com o mesmo nome. |
| CA1034 | [CA1034: Tipos aninhados não devem ser visíveis @ no__t-0 | Um tipo aninhado é um tipo declarado no escopo de outro tipo. Os tipos aninhados são úteis para encapsular detalhes de implementação privados do tipo de contenção. Usados para essa finalidade, os tipos aninhados não devem ser visíveis externamente. |
| CA1035 | [CA1035: Implementações ICollection têm membros fortemente tipados @ no__t-0 | Essa regra exige que implementações de ICollection forneçam membros fortemente tipados de forma que usuários não sejam obrigados a converter argumentos no tipo Object quando usarem a funcionalidade fornecida pela interface. Essa regra pressupõe que o tipo que implementa ICollection faça isso para gerenciar uma coleção de instâncias de um tipo mais forte que Object. |
| CA1036 | [CA1036: Substituir métodos em tipos comparáveis @ no__t-0 |Um público ou um tipo protegido implementa a interface System.IComparable. Ele não substitui Object.Equals nem sobrecarrega o operador específico da linguagem para igualdade, desigualdade, menor que ou maior que. |
| CA1038 | [CA1038: Enumeradores devem ser fortemente tipados @ no__t-0 | Essa regra exige que implementações de IEnumerator também forneçam uma versão fortemente tipada da propriedade Current de forma que usuários não sejam obrigados a converter o valor de retorno no tipo forte quando usarem a funcionalidade fornecida pela interface. |
| CA1039 | [CA1039: As listas são fortemente tipadas @ no__t-0 | Essa regra exige que implementações de IList forneçam membros fortemente tipados de forma que usuários não sejam obrigados a converter argumentos no tipo System.Object quando usarem a funcionalidade fornecida pela interface. |
| CA1040 |[CA1040: Evite interfaces vazias @ no__t-0 | As interfaces definem os membros que fornecem um contrato de comportamento ou de uso. A funcionalidade descrita pela interface pode ser adotada por qualquer tipo, independentemente de onde o tipo seja exibido na hierarquia de herança. Um tipo implementa uma interface fornecendo implementações para os membros da interface. Uma interface vazia não define membros; por isso, ela não define um contrato que pode ser implementado. |
| CA1041 | [CA1041: Forneça a mensagem ObsoleteAttribute @ no__t-0 | Um tipo ou um membro é marcado usando-se um atributo System.ObsoleteAttribute que não tem sua propriedade ObsoleteAttribute.Message especificada. Quando um tipo ou um membro marcado usando-se ObsoleteAttribute é compilado, a propriedade Message do atributo é exibida. Isso dá ao usuário informações sobre o tipo ou o membro obsoleto. |
| CA1043 | [CA1043: Usar argumento integral ou de cadeia de caracteres para indexadores @ no__t-0 | Os indicadores (ou seja, propriedades indexadas) devem usar tipos integrais ou de cadeia de caracteres no índice. Esses tipos normalmente são usados na indexação de estruturas de dados e aumentam a usabilidade da biblioteca. O uso do tipo Object deve ser restrito a esses casos em que o tipo integral ou de cadeia de caracteres específico não pode ser especificado no tempo de design. |
| CA1044 | [CA1044: As propriedades não devem ser somente gravação @ no__t-0 | Embora seja aceitável e normalmente necessário ter uma propriedade somente leitura, as diretrizes de design proíbem o uso de propriedades somente gravação. Isso é porque a permissão para que um usuário defina um valor e o impedimento posterior para ele exiba esse valor não dão nenhuma segurança. Além disso, sem acesso de leitura, o estado de objetos compartilhados não pode ser exibido, o que limita sua utilidade. |
| CA1045 |[CA1045: Não passe tipos por referência @ no__t-0 | A passagem de tipos por referência (usando out ou ref) requer experiência com ponteiros, compreensão das diferenças entre tipos de valor e tipos de referência e os métodos de tratamento que têm vários valores de retorno. Os arquitetos de biblioteca que projetam um público geral não devem esperar que os usuários façam o mestre de trabalho com parâmetros `out` ou `ref`. |
| CA1046 | [CA1046: Não sobrecarregar o operador Equals em tipos de referência @ no__t-0 | Para tipos de referência, a implementação padrão do operador de igualdade está quase sempre correta. Por padrão, duas referências só serão iguais se apontarem para o mesmo objeto. |
| CA1047 |[CA1047: Não declarar membros protegidos em tipos lacrados @ no__t-0 | Os tipos declaram membros protegidos de forma que a herança de tipos possa acessar ou substituir o membro. Por definição, os tipos vedados não podem ser lacrados, o que significa que os métodos protegidos em tipos lacrados não podem ser chamados. |
| CA1048 | [CA1048: Não declarar membros virtuais em tipos lacrados @ no__t-0 | Os tipos declaram métodos como virtuais de forma que a herança de tipos possa substituir a implementação do método virtual. Por definição, um tipo lacrado não pode ser herdado. Isso torna um método virtual em um tipo lacrado sem sentido. |
| CA1049 | [CA1049: Tipos que possuem recursos nativos devem ser descartáveis @ no__t-0 | Tipos que alocam recursos não gerenciados devem implementar IDisposable para permitir que os chamadores liberem esses recursos sob demanda e reduzir o tempo de vida dos objetos que contêm os recursos. |
| CA1050 | [CA1050: Declarar tipos em namespaces @ no__t-0 | Tipos são declarados em namespaces para evitar conflitos de nome e são uma maneira de organizar tipos relacionados em uma hierarquia de objetos. |
| CA1051 | [CA1051: Não declarar campos de instância visíveis @ no__t-0 | O principal uso de um campo deve ser um como um detalhe da implementação. Os campos devem ser privados ou internos e devem ser expostos usando-se propriedades. |
| CA1052 | [CA1052: Tipos de detentor estáticos devem ser lacrados @ no__t-0 | Um tipo público ou protegido contém apenas membros estáticos e não é declarado usando-se o modificador (Reference do C#) (NotInheritable). Um tipo que não é deve ser herdado deve ser marcado usando-se o modificador lacrado para evitar seu uso como um tipo de base. |
| CA1053 |[CA1053: Tipos de detentor estáticos não devem ter construtores @ no__t-0 | Um tipo público ou público aninhado declara apenas membros estáticos e tem um construtor padrão público ou protegido. O construtor é desnecessário porque chamar membros estáticos não exige uma instância do tipo. A sobrecarga de cadeia de caracteres deve chamar a sobrecarga do URI (Uniform Resource Identifier) usando-se o argumento de cadeia de caracteres por questões de segurança. |
| CA1054 | [CA1054: Os parâmetros de URI não devem ser cadeias de caracteres @ no__t-0 | Se um método utilizar uma representação de cadeia de caracteres de um URI, uma sobrecarga correspondente deverá ser fornecida utilizando uma instância da classe do URI, que oferece esses serviços de maneira segura e protegida. |
| CA1055 | [CA1055: Os valores de retorno de URI não devem ser cadeias de caracteres @ no__t-0 | Esta regra pressupõe que o método retorne um URI. Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A classe System.Uri fornece esses serviços de maneira segura. |
| CA1056 | [CA1056: As propriedades de URI não devem ser cadeias de caracteres @ no__t-0 | Esta regra pressupõe que a propriedade represente o URI. Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A classe System.Uri fornece esses serviços de maneira segura. |
| CA1057 | [CA1057: As sobrecargas de URI de cadeia de caracteres chamam o System. URI sobrecargas @ no__t-0 | Um tipo declara sobrecargas de método que diferem apenas pela substituição de um parâmetro de cadeia de caracteres com um parâmetro System.Uri. A sobrecarga que utiliza o parâmetro de cadeia de caracteres não chama a sobrecarga que utiliza o parâmetro do URI. |
| CA1058 | [CA1058: Os tipos não devem estender determinados tipos base](../code-quality/ca1058-types-should-not-extend-certain-base-types.md) | Um tipo visível externamente estende determinados tipos de base. Use uma das alternativas. |
| CA1059 |[CA1059: Os membros não devem expor determinados tipos concretos @ no__t-0 | Um tipo concreto é um tipo que tem uma implementação completa e, por isso, uma instância pode ser criada. Para permitir o uso difundido do membro, substitua o tipo concreto usando-se a interface sugerida. |
| CA1060 | [CA1060: Mover P/Invokes para a classe NativeMethods @ no__t-0 | Métodos de invocação da plataforma, como os marcados usando-se o atributo System.Runtime.InteropServices.DllImportAttribute, ou métodos definidos usando-se a palavra-chave Declare em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], acessam um código não gerenciado. Esses métodos devem ser da classe NativeMethods, SafeNativeMethods ou UnsafeNativeMethods. |
| CA1061 |[CA1061: Não ocultar métodos de classe base @ no__t-0 | Um método em um tipo de base permanece oculto por um método nomeado identicamente em um tipo derivado, quando a assinatura do parâmetro do método derivado difere apenas pelos tipos derivados de maneira mais fraca do que os tipos correspondentes na assinatura do parâmetro do método de base. |
| CA1062 | [CA1062: Validar argumentos de métodos públicos @ no__t-0 | Todos os argumentos de referência passados para os métodos visíveis externamente devem ser verificados em relação que serão nulos. |
| CA1063 | [CA1063: Implementar IDisposable corretamente @ no__t-0 | Todos os tipos IDisposable devem implementar o padrão Dispose corretamente. |
| CA1064 | [CA1064: As exceções devem ser públicas @ no__t-0 | Uma exceção interna só permanece visível dentro do próprio escopo interno. Depois que a exceção falha fora do escopo interno, somente a exceção de base pode ser usada para capturar a exceção. Se a exceção interna for herdada de <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>, o código externo não terá informações suficientes para saber o que fazer com a exceção. |
| CA1065 | [CA1065: Não gerar exceções em locais inesperados @ no__t-0 | Um método que não deve acionar exceções aciona uma exceção. |
| CA1068 | [CA1068: Os parâmetros de CancellationToken devem chegar ao último @ no__t-0 | Um método tem um parâmetro CancellationToken que não é o último parâmetro. |
| CA1200 | [CA1200: Evite usar marcas cref com um prefixo @ no__t-0 | O atributo [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) em uma marca de documentação XML significa "referência de código". Ele especifica que o texto interno da marca é um elemento de código, como um tipo, método ou propriedade. Evite usar marcas `cref` com prefixos, porque isso impede que o compilador Verifique as referências. Ele também impede que o IDE (ambiente de desenvolvimento integrado) do Visual Studio Localize e atualize essas referências de símbolo durante refatoração. |
| CA1300 | [CA1300: Especificar MessageBoxoptions @ no__t-0 | Para exibir corretamente uma caixa de mensagem para as culturas que usam uma ordem de leitura da direita para a esquerda, os membros RightAlign e RtlReading da enumeração MessageBoxOptions devem ser passados para o método Show. |
| CA1301 | [CA1301: Evite aceleradores duplicados @ no__t-0 | Uma tecla de acesso, também conhecida como acelerador, dá ao teclado acesso a um controle usando-se a tecla ALT. Quando vários controles têm chaves de acesso duplicadas, o comportamento da tecla de acesso não é bem definido. |
| CA1302 | [CA1302: Não codificar Cadeias de caracteres específicas de localidade @ no__t-0 | A enumeração System.Environment.SpecialFolder contém membros que fazem referência às pastas especiais do sistema. Os locais dessas pastas podem ter valores diferentes em diferentes sistemas operacionais; o usuário pode alterar alguns dos locais; e os locais são diferentes para cada linguagem. O método Environment.GetFolderPath retorna os locais associados à enumeração Environment.SpecialFolder, localizada e apropriada para o computador atualmente em execução. |
| CA1303 | [CA1303: Não passe literais como parâmetros localizados @ no__t-0 | Um método visível externamente passa um literal de cadeia de caracteres como um parâmetro para um construtor ou método .NET, e essa cadeia de caracteres deve ser localizável. |
| CA1304 | [CA1304: Especificar CultureInfo @ no__t-0 | Um método ou um construtor chama um membro que tem uma sobrecarga que aceita um parâmetro System.Globalization.CultureInfo, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro CultureInfo. Quando um objeto CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades. |
| CA1305 | [CA1305: Especificar IFormatProvider @ no__t-0 | Um método ou um construtor chama um ou mais membros que têm sobrecargas que aceitam um parâmetro System.IFormatProvider, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro IFormatProvider. Quando um objeto System.Globalization.CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades. |
| CA1306 | [CA1306: Definir localidade para tipos de dados @ no__t-0 | A localidade determina os elementos de apresentação específicos da cultura para dados, como a formatação usada para valores numéricos, símbolos de moeda e ordem de classificação. Ao criar um DataTable ou um DataSet, você deve definir explicitamente a localidade. |
| CA1307 | [CA1307: Especificar StringComparison @ no__t-0 | Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro StringComparison. |
| CA1308 |[CA1308: Normalizar cadeias de caracteres para @ no__t-0 maiúsculos | As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres não pode fazer uma viagem de ida e volta quando são convertidos em minúsculas. |
| CA1309 | [CA1309: Usar ordinal StringComparison @ no__t-0 | Uma operação de comparação de cadeia de caracteres não linguística não define o parâmetro StringComparison como Ordinal ou OrdinalIgnoreCase. Definindo-se explicitamente o parâmetro como StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, o código normalmente ganha velocidade, fica mais correto e se torna mais confiável. |
| CA1400 | [CA1400: Os pontos de entrada P/Invoke devem existir @ no__t-0 |Um método público ou protegido é marcado usando-se o atributo System.Runtime.InteropServices.DllImportAttribute. Não foi possível localizar a biblioteca não gerenciada ou não foi possível comparar o método a uma função na biblioteca. |
| CA1401 | [CA1401: P/Invokes não devem ser visíveis @ no__t-0 | Um método público ou protegido em um tipo público tem o atributo System.Runtime.InteropServices.DllImportAttribute (também implementado pela palavra-chave Declare em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Esses métodos não devem ser expostos. |
| CA1402 |[CA1402: Evite sobrecargas em interfaces visíveis COM @ no__t-0 | Quando os métodos sobrecarregados são expostos a clientes COM, apenas a primeira sobrecarga do método mantém seu nome. As sobrecargas subsequentes são renomeadas com exclusividade acrescentando-se ao nome um caractere de sublinhado (_) e um inteiro correspondente à ordem de declaração da sobrecarga. |
| CA1403 | [CA1403: Os tipos de layout automático não devem ser visíveis no COM @ no__t-0 | Um tipo de valor visível por COM é marcado usando-se o atributo System.Runtime.InteropServices.StructLayoutAttribute definido como LayoutKind.Auto. O layout desses tipos pode ser alterado entre as versões do .NET, o que interromperá clientes COM que esperam um layout específico. |
| CA1404 | [CA1404: Chamar GetLastError imediatamente após P/Invoke @ no__t-0 | É feita uma chamada para o método Marshal.GetLastWin32Error ou o equivalente [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] função GetLastError e a chamada imediatamente anterior não é para um sistema operacional invocar o método. |
| CA1405 | [CA1405: Os tipos base do tipo visível COM devem ser visíveis no COM @ no__t-0 | Um tipo visível por COM deriva de um tipo que não é visível por COM. |
| CA1406 |[CA1406: Evite argumentos Int64 para clientes Visual Basic 6 @ no__t-0 | Os clientes COM do Visual Basic 6 não podem acessar inteiros de 64 bits. |
| CA1407 |[CA1407: Evite membros estáticos em tipos visíveis do COM @ no__t-0 | COM não dá suporte para métodos estáticos. |
| CA1408 | [CA1408: Não usar AutoDual ClassInterfaceType @ no__t-0 | Tipos que usam uma interface dupla permitem que clientes sejam associados a um layout de interface específico. Todas as alterações feitas em uma versão futura do layout do tipo ou de qualquer tipo de base interromperão clientes COM associados à interface. Por padrão, se o atributo ClassInterfaceAttribute não for especificado, será usada uma interface somente de expedição. |
| CA1409 | [CA1409: Tipos visíveis com devem ser creatable @ no__t-0 |Um tipo de referência marcado especificamente como visível para COM contém um construtor parametrizado público, mas não contém um construtor padrão público (sem parâmetros). Um tipo sem um construtor padrão público não pode ser criado por clientes COM. |
| CA1410 | [CA1410: Os métodos de registro COM devem ser correspondentes a @ no__t-0 | Um tipo declara um método marcado usando o atributo System.Runtime.InteropServices.ComRegisterFunctionAttribute, mas não declara um método marcado usando o atributo System.Runtime.InteropServices.ComUnregisterFunctionAttribute, ou vice-versa. |
| CA1411 | [CA1411: Os métodos de registro COM não devem ser visíveis @ no__t-0 | Um método marcado usando-se o atributo System.Runtime.InteropServices.ComRegisterFunctionAttribute ou o atributo System.Runtime.InteropServices.ComUnregisterFunctionAttribute permanece visível externamente. |
| CA1412 | [CA1412: Marcar interfaces de origem como IDispatch @ no__t-0 | Um tipo é marcado usando-se o atributo System.Runtime.InteropServices.ComSourceInterfacesAttribute, e pelo menos uma das interfaces especificadas não está marcada usando-se o atributo System.Runtime.InteropServices.InterfaceTypeAttribute definido como ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413: Evite campos não públicos em tipos de valores visíveis do COM @ no__t-0 | Os campos de instância não pública dos tipos de valor visíveis por COM permanecem visíveis para clientes COM. Revise o conteúdo dos campos em busca de informações que não devem ser expostas, ou isso terá efeitos não intencionais sobre o design ou a segurança. |
| CA1414 | [CA1414: Marcar argumentos P/Invoke boolianos com MarshalAs @ no__t-0 | O tipo de dados Booliano tem várias representações em código não gerenciado. |
| CA1415 | [CA1415: Declarar P/Invokes corretamente @ no__t-0 | Esta regra procura declarações do método de invocação do sistema operacional com funções [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] como destino que tenham um ponteiro para um parâmetro de estrutura OVERLAPPED e o parâmetro gerenciado correspondente não seja um ponteiro para uma estrutura System.Threading.NativeOverlapped. |
| CA1500 | [CA1500: Nomes de variáveis não devem corresponder a nomes de campos @ no__t-0 | Um método de instância declara um parâmetro ou uma variável local cujo nome corresponde a um campo da instância do tipo declarante, o que leva a erros. |
| CA1501 | [CA1501: Evitar herança excessiva @ no__t-0 | Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter. |
| CA1502 | [CA1502: Evitar complexidade excessiva @ no__t-0 | Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais. |
| CA1504 | [CA1504: Revisar nomes de campo enganosos @ no__t-0 | O nome de um campo de instância começa com "s _", ou o nome do campo estático (compartilhado no Visual Basic) começa com "m _". |
| CA1505 | [CA1505: Evitar código não passível de manutenção @ no__t-0 | Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design. |
| CA1506 |[CA1506: Evite o acoplamento de classe em excesso @ no__t-0 | Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém. |
| CA1600 | [CA1600: Não usar prioridade de processo ocioso @ no__t-0 | Não defina a prioridade do processo como Ocioso. Os processos que têm System.Diagnostics.ProcessPriorityClass.Idle ocuparão a CPU quando estariam ociosos e, assim, bloquearão a espera. |
| CA1601 | [CA1601: Não use temporizadores que impeçam alterações de estado de energia @ no__t-0 | A atividade periódica de alta frequência manterá a CPU ocupada e interferirá nos temporizadores ociosos que economizam energia e desligam monitores e discos rígidos. |
| CA1700 | [CA1700: Não Nomeie os valores de enumeração como ' reservado ' ](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | Esta regra pressupõe que um membro da enumeração que tenha um nome que contém "reserved" não é usado atualmente, mas é um espaço reservado a ser renomeado ou removido em uma versão futura. Renomear ou remover um membro é uma alteração drástica. |
| CA1701 | [CA1701: As palavras compostas da cadeia de recursos devem ser maiúsculas e minúsculas no no__t-0 | Cada palavra na cadeia de caracteres de recurso é dividida em tokens com base em maiúsculas. Cada combinação contígua de dois tokens é verificada pela biblioteca do verificador ortográfico da Microsoft. Se reconhecidas, as palavras produzirão uma violação da regra. |
| CA1702 | [CA1702: Palavras compostas devem estar em maiúsculas e minúsculas em @ no__t-0 | O nome de um identificador contém várias palavras e pelo menos uma das palavras parece ser uma palavra composta que não tem maiúsculas corretas. |
| CA1703 | [CA1703: As cadeias de caracteres de recurso devem ser escritas corretamente @ no__t-0 | Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft. |
| CA1704 | [CA1704: Os identificadores devem ser escritos corretamente @ no__t-0 | O nome de um identificador visível externamente contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft. |
| CA1707 | [CA1707: Identificadores não devem conter sublinhados @ no__t-0 | Por convenção, os nomes de identificador não contêm o caractere de sublinhado (_). Esta regra verifica namespaces, tipos, membros e parâmetros. |
| CA1708 | [CA1708: Os identificadores devem ser diferentes em mais do que caso @ no__t-0 | Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas. |
| CA1709 | [CA1709: Os identificadores devem ser totais corretamente @ no__t-0 | Por convenção, nomes de parâmetro usam maiúsculas, namespace e tipo, e nomes de membro usam maiúsculas Pascal. |
| CA1710 | [CA1710: Os identificadores devem ter o sufixo correto @ no__t-0 |Por convenção, os nomes de tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, têm um sufixo associado ao tipo de base ou à interface. |
| CA1711 | [CA1711: Os identificadores não devem ter o sufixo incorreto @ no__t-0 | Por convenção, apenas os nomes de tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, devem terminar com sufixos reservados específicos. Outros nomes de tipo não devem usar esses sufixos reservados. |
| CA1712 | [CA1712: Não Prefixe valores de enumeração com o nome de tipo @ no__t-0 | Os nomes dos membros de enumeração não são prefixados usando-se o nome de tipo porque as ferramentas de desenvolvimento devem fornecer informações de tipo. |
| CA1713 | [CA1713: Os eventos não devem ter o prefixo before ou After @ no__t-0 | O nome de um evento começa com "Before" ou "After". Para nomear eventos relacionados acionados em uma sequência específica, use o presente ou o pretérito para indicar a posição relativa na sequência de ações. |
| CA1714 | [CA1714: Enumerações de sinalizadores devem ter nomes no plural @ no__t-0 | Uma enumeração pública tem o atributo System.FlagsAttribute, e seu nome não termina com "s". Tipos marcados usando FlagsAttribute têm nomes que estão no plural porque o atributo indica que mais de um valor pode ser especificado. |
| CA1715 | [CA1715: Os identificadores devem ter o prefixo correto @ no__t-0 | O nome de uma interface visível externamente não começa com "I" em maiúsculas. O nome de um parâmetro de tipo genérico em um tipo visível externamente ou método não começa com um "T" em maiúsculas. |
| CA1716 | [CA1716: Os identificadores não devem corresponder às palavras-chave @ no__t-0 | Um nome de namespace ou um nome de tipo corresponde a uma palavra-chave reservada em uma linguagem de programação. Os identificadores de namespaces e tipos não devem corresponder a palavras-chave definidas por com o Common Language Runtime como destino. |
| CA1717 | [CA1717: Somente enums FlagsAttribute devem ter nomes no plural @ no__t-0 | As convenções de nomenclatura determinam que um nome no plural para uma enumeração indica que mais de um valor de enumeração pode ser especificado ao mesmo tempo. |
| CA1719 | [CA1719: Nomes de parâmetros não devem corresponder a nomes de membro @ no__t-0 | Um nome de parâmetro deve informar o significado de um parâmetro e um nome de membro deve informar o significado de um membro. Seria um design raro se eles fossem iguais. A nomenclatura de um parâmetro com o mesmo nome do membro não é intuitiva e dificulta o uso da biblioteca. |
| CA1720 |[CA1720: Identificadores não devem conter nomes de tipo @ no__t-0 | O nome de um parâmetro em um membro visível externamente contém um nome de tipo de dados, ou o nome de um membro visível externamente contém um nome de tipo de dados específico da linguagem. |
| CA1721 | [CA1721: Os nomes de propriedade não devem corresponder aos métodos get @ no__t-0 |O nome de um membro público ou protegido começa com "Get" e, de outra forma, corresponde ao nome de uma propriedade pública ou protegida. Métodos "Get" e propriedades devem ter nomes que diferenciem claramente a função. |
| CA1722 | [CA1722: Os identificadores não devem ter o prefixo incorreto @ no__t-0 | Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico. |
| CA1724 | [CA1724: Nomes de tipos não devem corresponder a namespaces @ no__t-0 | Os nomes de tipo não devem corresponder aos nomes dos namespaces do .NET. A violação dessa regra pode reduzir a usabilidade da biblioteca. |
| CA1725 | [CA1725: Nomes de parâmetros devem corresponder à declaração base @ no__t-0 | A nomenclatura consistente dos parâmetros em uma hierarquia de substituição aumenta a usabilidade das substituições de método. Um nome de parâmetro em um método derivado diferente do nome na declaração de base pode causar confusão em relação à possibilidade do método ser uma substituição do método de base ou de uma nova sobrecarga do método. |
| CA1726 | [CA1726: Usar termos preferenciais @ no__t-0 | O nome de um identificador visível externamente inclui um termo para o qual existe um termo preferido, alternativo. Como alternativa, o nome inclui o termo "Flag" ou "Flags". |
| CA1800 | [CA1800: Não converter desnecessariamente @ no__t-0 | As conversões duplicadas diminui o desempenho, especialmente quando as conversões são realizadas em instruções de iteração compactas. |
| CA1801 | [CA1801: Examinar parâmetros não utilizados @ no__t-0 | Uma assinatura de método inclui um parâmetro que não é usado no corpo do método. |
| CA1802 |[CA1802: Usar literais onde @ no__t-0 apropriado |Um campo é declarado estático e somente leitura (Shared e ReadOnly no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), e é inicializado usando-se um valor computável no tempo de compilação. Como o valor que é atribuído ao campo de destino é computável no tempo de compilação, altere a declaração para const (Const em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) para que o valor é calculado em tempo de compilação em vez de em tempo de execução de campo. |
| CA1804 | [CA1804: Remover locais não utilizados @ no__t-0 | As variáveis locais não utilizadas e as atribuições desnecessárias aumentam o tamanho de um assembly e diminuem o desempenho. |
| CA1806 | [CA1806: Não ignore os resultados do método @ no__t-0 | Um novo objeto é criado, mas nunca é usado; ou um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres jamais é usada; um método ou COM ou P/Invoke retorna um HRESULT ou um código de erro que nunca é usado. |
| CA1809 |[CA1809: Evite locais em excesso no @ no__t-0 | Uma otimização de desempenho comum é armazenar um valor em um registro de processador, em vez da memória, algo conhecido como "registro do valor". Para aumentar a chance de que todas as variáveis locais sejam cancelado, limite o número de variáveis locais a 64. |
| CA1810 | [CA1810: Inicialize os campos estáticos do tipo de referência em linha @ no__t-0 | Quando um tipo declara um construtor estático explícito, o compilador JIT (just-in-time) adiciona uma verificação a cada método estático e construtor de instância do tipo para garantir que o construtor estático tenha sido chamado anteriormente. As verificações de construtor estático podem diminuir o desempenho. |
| CA1811 | [CA1811: Evite código particular não chamado @ no__t-0 | Um membro particular ou interno (no nível de assembly) não tem chamadores no assembly; ele não é invocado pelo Common Language Runtime e não é invocado por um representante. |
| CA1812 | [CA1812: Evite classes internas não instanciadas @ no__t-0 | Uma instância de um tipo no nível de assembly não é criada pelo código no assembly. |
| CA1813 | [CA1813: Evitar atributos não lacrados @ no__t-0 | O .NET fornece métodos para recuperar atributos personalizados. Por padrão, esses métodos pesquisam a hierarquia de herança do atributo. A validação do atributo elimina a pesquisa na hierarquia de herança e pode melhorar o desempenho. |
| CA1814 | [CA1814: Prefira matrizes denteadas sobre multidimensional @ no__t-0 | Uma matriz denteada é uma matriz cujos elementos são matrizes. As matrizes que constituem os elementos podem ter tamanhos diferentes, o que leva a menos espaço desperdiçado para alguns conjuntos de dados. |
| CA1815 | [CA1815: Substituir equals e operador equals em tipos de valor](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | Para tipos de valor, a implementação herdada de Equals usa a biblioteca Reflection e compara o conteúdo de todos os campos. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários comparem ou classifiquem instâncias, ou usem instâncias como chaves de tabela de hash, o tipo de valor deverá implementar Equals. |
| CA1816 | [CA1816: Chame GC. SuppressFinalize corretamente @ no__t-0 | Um método que é uma implementação de Dispose não chama GC. SuppressFinalize; ou um método que não é uma implementação de Dispose chama GC. SuppressFinalize; ou um método chama GC. SuppressFinalize e passa algo que não seja isso (Me no Visual Basic). |
| CA1819 | [CA1819: Propriedades não devem retornar matrizes @ no__t-0 | As matrizes retornadas por propriedades não estão protegidas contra a gravação, mesmo quando a propriedade é somente leitura. Para manter a matriz à prova de adulteração, a propriedade deve retornar uma cópia da matriz. Normalmente, os usuários não compreenderão as implicações adversas no desempenho de chamar uma propriedade assim. |
| CA1820 | [CA1820: Teste para cadeias de caracteres vazias usando o comprimento da cadeia @ no__t-0 | A comparação de cadeias de caracteres usando-se a propriedade String.Length ou o método String.IsNullOrEmpty é significativamente mais rápida do que o uso de Equals. |
| CA1821 | [CA1821: remova os finalizadores vazios](../code-quality/ca1821-remove-empty-finalizers.md) | Sempre que possível, evite finalizadores por conta da sobrecarga adicional no desempenho envolvida no acompanhamento do tempo de vida do objeto. Um finalizador vazio incorre na sobrecarga adicionada e não oferece benefícios. |
| CA1822 |[CA1822: Marcar Membros como estáticos @ no__t-0 | Os membros que não acessam dados da instância ou os métodos da instância de chamada podem ser marcados como estáticos (Shared no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Depois que você marcar os métodos como estáticos, o compilador emitirá sites de chamada não virtuais para esses membros. Isso pode proporcionar um ganho de desempenho mensurável para o código sensível ao desempenho. |
| CA1823 | [CA1823: Evite campos particulares não utilizados @ no__t-0 | Foram detectados campos particulares que aparentemente não são acessados no assembly. |
| CA1824 |[CA1824: Marcar assemblies com NeutralResourcesLanguageAttribute @ no__t-0 | O atributo NeutralResourcesLanguage informa o Gerenciador de recursos da linguagem que foi usada para exibir os recursos de uma cultura neutra para um assembly. Isso melhora o desempenho da pesquisa para o primeiro recurso carregado e pode reduzir o conjunto de trabalho. |
| CA1825 |[CA1825: Evitar alocações de matriz de comprimento zero @ no__t-0 | A inicialização de uma matriz de comprimento zero leva à alocação de memória desnecessária. Em vez disso, use a instância de matriz vazia estaticamente alocada chamando <xref:System.Array.Empty%2A?displayProperty=nameWithType>. A alocação de memória é compartilhada entre todas as invocações desse método. |
| CA1900 | [CA1900: Os campos de tipo de valor devem ser portáteis @ no__t-0 | Essa regra verifica se as estruturas declaradas usando-se o layout explícito serão alinhadas corretamente durante a realização de marshaling para o código não gerenciado em sistemas operacionais de 64 bits. |
| CA1901 | [CA1901: As declarações P/Invoke devem ser portáteis @ no__t-0 | Essa regra avalia o tamanho de cada parâmetro e o valor de retorno de um P/Invoke, além de verificar se o tamanho do parâmetro está correto durante a realização de marshaling para código não gerenciado em sistemas operacionais 32 e 64 bits. |
| CA1903 | [CA1903: Usar somente a API da estrutura de destino @ no__t-0 | Um membro ou um tipo está usando um membro ou um tipo que foi introduzido em um service pack não incluído com a estrutura de destino do projeto. |
| CA2000 | [CA2000: Descartar objetos antes de perder o escopo @ no__t-0 | Como pode ocorrer um evento excepcional que impedirá a execução do finalizador de um objeto, o objeto deve ser explicitamente descartado antes que todas as referências a ele estejam fora do escopo. |
| CA2001 | [CA2001: Evite chamar métodos problemáticos @ no__t-0 | Um membro chama um método potencialmente perigoso ou problemático. |
| CA2002 |[CA2002: Não bloquear objetos com identidade fraca @ no__t-0 |Diz-se que um objeto tem uma identidade fraca quando puder ser acessado diretamente em todos os limites de domínio do aplicativo. Um thread que tente adquirir um bloqueio em um objeto com uma identidade fraca pode ser bloqueado por um segundo thread em um domínio de aplicativo diferente com um bloqueio no mesmo objeto. |
| CA2003 |[CA2003: Não tratar fibras como threads @ no__t-0 | Um thread gerenciado está sendo tratado como um thread do [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]. |
| CA2004 | [CA2004: Remova as chamadas para GC. KeepAlive @ no__t-0 | Se você converter no uso de SafeHandle, remova todas as chamadas para GC.KeepAlive (objeto). Nesse caso, as classes não precisarão chamar GC.KeepAlive. Isso pressupõe que elas não tenham um finalizador, mas dependam de SafeHandle para finalizar o identificador do sistema operacional para elas. |
| CA2006 | [CA2006: Usar o SafeHandle para encapsular recursos nativos @ no__t-0 | O uso de IntPtr em código gerenciado pode indicar um problema de segurança e confiabilidade em potencial. Todos os usos de IntPtr devem ser examinados para determinar se o uso de um SafeHandle, ou tecnologia semelhante, é necessário em seu lugar. |
| CA2007 | [CA2007: Não aguardar diretamente uma tarefa @ no__t-0 | Um método assíncrono [aguarda](/dotnet/csharp/language-reference/keywords/await) um <xref:System.Threading.Tasks.Task> diretamente. Quando um método assíncrono aguarda um <xref:System.Threading.Tasks.Task> diretamente, a continuação ocorre no mesmo thread que criou a tarefa. Esse comportamento pode ser dispendioso em termos de desempenho e pode resultar em um deadlock no thread da interface do usuário. Considere chamar <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> para sinalizar sua intenção de continuação. |
| CA2100 | [CA2100: Examinar consultas SQL em busca de vulnerabilidades de segurança @ no__t-0 | Um método define a propriedade System.Data.IDbCommand.CommandText usando uma cadeia de caracteres criada com base em um argumento da cadeia de caracteres para o método. Esta regra pressupõe que o argumento da cadeia de caracteres contenha a entrada do usuário. Uma cadeia de caracteres de comando SQL criada com base na entrada do usuário é vulnerável a ataques de injeção SQL. |
| CA2101 |[CA2101: Especificar o marshaling para argumentos de cadeia de caracteres P/Invoke @ no__t-0 | Um membro de invocação da plataforma permite chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres e não realiza marshaling da cadeia de caracteres explicitamente. Isso pode causar uma vulnerabilidade de segurança em potencial. |
| CA2102 | [CA2102: Capturar exceções não CLSCompliant em manipuladores gerais @ no__t-0 | Um membro em um assembly que não é marcado usando-se o RuntimeCompatibilityAttribute ou que é marcado como RuntimeCompatibility (WrapNonExceptionThrows = false) contém um bloco de captura que trata System.Exception e não contém um bloco de captura geral imediatamente posterior. |
| CA2103 | [CA2103: Examinar segurança imperativa @ no__t-0 |Um método usa segurança obrigatória e pode construir a permissão usando as informações de estado ou os valores de retorno que podem ser alterados desde que a demanda esteja ativa. Use a segurança declarativa sempre que possível. |
| CA2104 |[CA2104: Não declarar tipos de referência mutáveis somente leitura @ no__t-0 | Um tipo visível externamente contém um campo somente leitura visível externamente que é um tipo de referência mutável. Um tipo mutável é um tipo cujos dados da instância podem ser modificados. |
| CA2105 | [CA2105: Os campos de matriz não devem ser somente leitura @ no__t-0 |Quando você aplica o modificador somente leitura (ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) a um campo que contém uma matriz, o campo não pode ser alterado para fazer referência a uma matriz diferente. No entanto, os elementos da matriz que são armazenados em um campo somente leitura podem ser alterados. |
| CA2106 | [CA2106: Declarações seguras @ no__t-0 | Um método declara uma permissão e nenhuma verificação de segurança é realizada no chamador. A declaração de uma permissão de segurança sem realizar verificações de segurança pode deixar uma fraqueza de segurança explorável no código. |
| CA2107 | [CA2107: Revisar a negação e permitir somente o uso @ no__t-0 |O método PermitOnly e as ações de segurança CodeAccessPermission. Deny devem ser usados somente por aqueles que têm conhecimento avançado sobre a segurança do .NET. O código que usa essas ações de segurança deve passar por uma revisão de segurança. |
| CA2108 | [CA2108: Examinar a segurança declarativa nos tipos de valor @ no__t-0 | Um tipo de valor público ou protegido é resguardado por acesso a dados ou exigências de vínculo. |
| CA2109 | [CA2109: Examinar manipuladores de eventos visíveis @ no__t-0 | Um método público ou protegido de tratamento de eventos foi detectado. Os métodos de tratamento de eventos não devem ser expostos, a menos que seja absolutamente necessário. |
| CA2111 |[CA2111: Os ponteiros não devem ser visíveis @ no__t-0 | Um ponteiro não é privado, interno ou somente leitura. Um código mal-intencionado pode alterar o valor do ponteiro, o que pode dar acesso a locais arbitrários na memória ou causar falhas no aplicativo ou no sistema. |
| CA2112 | [CA2112: Os tipos protegidos não devem expor os campos @ no__t-0 | Um tipo público ou protegido contém campos públicos e é protegido por exigências de vínculo. Se tiver acesso a uma instância de um tipo protegido por uma exigência de vínculo, o código não precisará atender à exigência de vínculo para acessar os campos do tipo. |
| CA2114 | [CA2114: A segurança do método deve ser um superconjunto do tipo @ no__t-0 | Um método não deve ter segurança declarativa no nível do método e no nível do tipo para a mesma ação. |
| CA2115 | [CA2115: Chame GC. KeepAlive ao usar recursos nativos @ no__t-0 | Esta regra detecta erros que podem ocorrer porque um recurso não gerenciado está sendo finalizado, enquanto ainda está sendo usado em código não gerenciado. |
| CA2116 | [CA2116: Os métodos APTCA só devem chamar os métodos APTCA @ no__t-0 |Quando APTCA AllowPartiallyTrustedCallersAttribute () estiver presente em um assembly totalmente confiável e o assembly executar código em outro assembly que não permita chamadores parcialmente confiáveis, será possível uma exploração de segurança. |
| CA2117 | [CA2117: Os tipos APTCA só devem estender os tipos base APTCA @ no__t-0 | Quando APTCA estiver presente em um assembly totalmente confiável e um tipo no assembly for herdado de um tipo que não permita chamadores parcialmente confiáveis, será possível uma exploração de segurança. |
| CA2118 | [CA2118: Examinar o uso de SuppressUnmanagedCodeSecurityAttribute @ no__t-0 |SuppressUnmanagedCodeSecurityAttribute altera o comportamento do sistema de segurança padrão para membros que executem código não gerenciado que usa interoperabilidade COM ou invocação do sistema operacional. Esse atributo é usado principalmente para aumentar o desempenho; no entanto, os ganhos de desempenho acompanham riscos de segurança significativos. |
| CA2119 | [CA2119: Métodos de lacre que satisfazem interfaces privadas @ no__t-0 | Um tipo público herdável fornece uma implementação de método substituível de uma interface (Friend no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) interna. Para corrigir uma violação dessa regra, evite que o método seja substituído fora do assembly. |
| CA2120 | [CA2120: Construtores de serialização segura @ no__t-0 | Esse tipo tem um construtor que utiliza um objeto System.Runtime.Serialization.SerializationInfo e um objeto System.Runtime.Serialization.StreamingContext (a assinatura do construtor de serialização). Esse construtor não é protegido por uma verificação de segurança, mas um ou mais dos construtores regulares no tipo são protegidos. |
| CA2121 | [CA2121: Construtores estáticos devem ser particulares](../code-quality/ca2121-static-constructors-should-be-private.md) | O sistema chama o construtor estático antes que a primeira instância do tipo seja criada ou que outros membros estáticos sejam referenciados. Se não for privado, um construtor estático poderá ser chamado por um código diferente do sistema. Dependendo das operações realizadas no construtor, isso pode causar um comportamento inesperado. |
| CA2122 | [CA2122: Não expor indiretamente métodos com demandas de link @ no__t-0 | Um membro público ou protegido tem exigências de vínculo e é chamado por um membro que não realiza nenhuma verificação de segurança. Uma exigência de vínculo verifica as permissões apenas do chamador imediato. |
| CA2123 | [CA2123: A substituição das demandas de link deve ser idêntica à base @ no__t-0 | Esta regra compara um método ao método de base, que é uma interface ou um método virtual em outro tipo e, em seguida, compara as exigências de vínculo em cada um. Se essa regra for violada, um chamador mal-intencionado poderá ignorar a exigência de vínculo apenas chamando o método não seguro. |
| CA2124 | [CA2124: Encapsular cláusulas finally vulneráveis em try externo @ no__t-0 | Um método público ou protegido contém um bloco try/finally. O bloco finally aparentemente redefine o estado de segurança não está incluído em um bloco finally. |
| CA2126 | [CA2126: Solicitações de link de tipo exigem demandas de herança @ no__t-0 | Um tipo sem lacre público é protegido usando-se uma exigência de link e tem um método substituível. Nem o tipo nem o método é protegido usando-se uma exigência de herança. |
| CA2127 | [CA2136: Os membros não devem ter anotações de transparência em conflito @ no__t-0 | Código crítico não pode ocorrer em um assembly 100 por cento transparente. Esta regra analisa assemblies 100 por cento transparente para todas as anotações de SecurityCritical no tipo, campo e os níveis de método. |
| CA2128 |[CA2147: Métodos transparentes não podem usar declarações de segurança @ no__t-0 | Esta regra analisa todos os métodos e tipos em um assembly que é 100 por cento transparente ou misto transparente/crítico e sinaliza o uso declarativo ou obrigatório de Assert. |
| CA2129 | [CA2140: O código transparent não deve fazer referência a itens críticos de segurança @ no__t-0 | Métodos que são marcados por SecurityTransparentAttribute chamam membros públicos marcados como SecurityCritical. Esta regra analisa todos os métodos e tipos em um assembly que seja transparente/crítico misto, e sinaliza todas as chamadas de código transparente para o código crítico não público que não estejam marcadas como SecurityTreatAsSafe. |
| CA2130 | [CA2130: As constantes críticas de segurança devem ser transparentes no @ no__t-0 | A imposição de transparência não é imposta para valores constantes porque compiladores têm valores constantes internos de modo que nenhuma pesquisa seja necessária no tempo de execução. Os campos constantes devem ter segurança transparente de forma que os revisores de código não pressuponham que o código transparente não pode acessar a constante. |
| CA2131 | [CA2131: Tipos críticos de segurança podem não participar do tipo equivalentes @ no__t-0 | Um tipo participa da equivalência do tipo e o próprio tipo, ou um membro ou campo do tipo, é marcado usando-se o atributo SecurityCriticalAttribute. Esta regra ocorre em qualquer tipo crítico ou em tipos que contenham métodos críticos ou campos que estejam participando da equivalência do tipo. Ao detectar um tipo assim, o CLR não o carrega com um TypeLoadException em tempo de execução. Normalmente, essa regra só é acionada quando usuários implementam equivalência de tipo manualmente, em vez de depender de tlbimp e dos compiladores para fazer a equivalência do tipo. |
| CA2132 | [CA2132: Os construtores padrão devem ser pelo menos tão críticos quanto os construtores padrão do tipo base @ no__t-0 |Os tipos e os membros que têm o SecurityCriticalAttribute não podem ser usados pelo código de aplicativo do Silverlight. Os tipos de segurança crítica e os membros só podem ser usados por código confiável no .NET Framework para a biblioteca de classes do Silverlight. Como uma construção pública ou protegida em uma classe derivada deve ter a mesma transparência maior que sua classe base, uma classe em um aplicativo não pode ser derivada de uma classe marcada como SecurityCritical. |
| CA2133 | [CA2133: Delegados devem ser associados a métodos com transparência consistente @ no__t-0 | Esse aviso é acionado em um método que associa um representante que foi marcado usando-se o SecurityCriticalAttribute para um método transparente ou marcado usando-se SecuritySafeCriticalAttribute. O aviso também é acionado em um método que associa um representante transparente ou de segurança crítica a um método crítico. |
| CA2134 | [CA2134: Os métodos devem manter a transparência consistente ao substituir os métodos base @ no__t-0 |Essa regra é acionada quando um método marcado usando-se o SecurityCriticalAttribute substitui um método transparente ou marcado usando-se SecuritySafeCriticalAttribute. A regra também é acionada quando um método transparente ou marcado usando-se SecuritySafeCriticalAttribute substitui um método marcado usando-se um SecurityCriticalAttribute. A regra é aplicada durante a substituição de um método virtual ou a implementação de uma interface. |
| CA2135 | [CA2135: Os assemblies de nível 2 não devem conter LinkDemands @ no__t-0 | LinkDemands são preteridos no conjunto de regras de segurança nível 2. Em vez de usar LinkDemands para impor a segurança em tempo de compilação JIT, marque os métodos, os tipos e os campos usando o atributo SecurityCriticalAttribute. |
| CA2136 | [CA2136: Os membros não devem ter anotações de transparência em conflito @ no__t-0 | Os atributos de transparência são aplicados com base nos elementos de código de escopo maior a elementos de escopo menor. Os atributos de transparência dos elementos de código que têm escopo maior têm precedência sobre atributos de transparência dos elementos de código contidos no primeiro elemento. Por exemplo, uma classe marcada usando-se o atributo SecurityCriticalAttribute não pode conter um método marcado usando-se o atributo SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137: Os métodos Transparent devem conter somente IL verificável @ no__t-0 | Um método contém código não verificável ou retorna um tipo por referência. Esta regra é acionada em tentativas por código transparente de segurança para executar MISL (Microsoft Intermediate Language) não verificável. Entretanto, a regra não contém um verificador de IL completo e, em vez disso, usa heurística para capturar a maioria das violações de verificação de MSIL. |
| CA2138 | [CA2138: Os métodos Transparent não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity @ no__t-0 | Um método de segurança transparente chama um método marcado usando-se o atributo SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139: Métodos transparentes não podem usar o atributo HandleProcessCorruptingExceptions @ no__t-0 | Esta regra é acionada por qualquer método que seja transparente e tenta tratar uma exceção de corrompimento de processo usando o atributo HandleProcessCorruptedStateExceptionsAttribute. Uma exceção de corrompimento de processo é uma classificação de exceção do CLR versão 4.0 de exceções, como AccessViolationException. O atributo HandleProcessCorruptedStateExceptionsAttribute só pode ser usado por métodos de segurança crítica e será ignorado se for aplicado a um método transparente. |
| CA2140 | [CA2140: O código transparent não deve fazer referência a itens críticos de segurança @ no__t-0 | Um elemento de código marcado usando-se o atributo SecurityCriticalAttribute é crítico para segurança. Um método transparente não pode usar um elemento crítico para segurança. Se um tipo transparente tentar usar um tipo crítico de segurança, um TypeAccessException, um MethodAccessException ou um FieldAccessException será acionado. |
| CA2141 |[CA2141: métodos transparentes não devem atender a LinkDemands](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | Um método transparente de segurança chama um método em um assembly que não foi marcado usando-se o APTCA ou um método transparente de segurança atende a um LinkDemand para um tipo ou um método. |
| CA2142 | [CA2142: O código transparent não deve ser protegido com LinkDemands @ no__t-0 | Esta regra é acionada em métodos transparentes que exigem LinkDemands para serem acessados. O código transparente de segurança não deve ser responsável por verificar a segurança de uma operação e, assim, não deve exigir permissões. |
| CA2143 | [CA2143: Os métodos transparentes não devem usar as demandas de segurança @ no__t-0 | O código transparente de segurança não deve ser responsável por verificar a segurança de uma operação e, assim, não deve exigir permissões. O código transparente de segurança deve usar demandas completas para tomar decisões de segurança e o código crítico de segurança não deve confiar no código transparente para fazer a demanda completa. |
| CA2144 | [CA2144: O código transparent não deve carregar assemblies de matrizes de bytes @ no__t-0 | A revisão de segurança para o código transparente não é tão completo quanto a revisão de segurança para o código crítico porque o código transparente não pode realizar ações confidenciais de segurança. Os assemblies carregados a partir de uma matriz de bytes podem não ser observados no código transparente e essa matriz de bytes pode conter código crítico ou código crítico de segurança mais importante, que precisa ser auditado. |
| CA2145 | [CA2145: Os métodos Transparent não devem ser decorados com SuppressUnmanagedCodeSecurityAttribute @ no__t-0 | Os métodos decorados pelo atributo SuppressUnmanagedCodeSecurityAttribute têm um LinkDemand implícito colocado em qualquer método que o chame. Este LinkDemand requer que o código de chamada seja crítico de segurança. A marcação do método que usa SuppressUnmanagedCodeSecurity usando o atributo SecurityCriticalAttribute torna esse requisito mais óbvio para chamadores do método. |
| CA2146 | [CA2146: Os tipos devem ser pelo menos tão críticos quanto seus tipos de base e interfaces @ no__t-0 | Esta regra é acionada quando um tipo derivado tem um atributo de transparência de segurança que não é tão crítico quanto seu tipo de base ou interface implementada. Apenas os tipos críticos podem derivar os tipos de base críticos ou implementar interfaces críticos, e apenas os tipos críticos ou de segurança crítica podem derivar dos tipos de base críticos de segurança ou implementar interfaces críticas de segurança. |
| CA2147 |[CA2147: Métodos transparentes não podem usar declarações de segurança @ no__t-0 | O código que é marcado como SecurityTransparentAttribute não recebe permissões suficientes para declarar. |
| CA2149 | [CA2149: Os métodos Transparent não devem chamar o código nativo @ no__t-0 | Esta regra é aciona em qualquer método transparente chamado diretamente no código nativo (por exemplo, por meio de um P/Invoke). As violações dessa regra resultam em um MethodAccessException no modelo de transparência de nível 2 e uma demanda completa para UnmanagedCode no modelo de transparência de nível 1. |
| CA2151 |[CA2151: Os campos com tipos críticos devem ser críticos para segurança @ no__t-0 | Para usar tipos de segurança crítica, o código que faz referência ao tipo deve ser de segurança crítica ou de segurança crítica segura. Isso será verdadeiro mesmo que a referência seja indireta. Por isso, ter um campo de segurança transparente ou de segurança crítica é enganoso porque o código transparente continuará incapaz de acessar o campo. |
| CA2200 | [CA2200: Relançar para preservar detalhes da pilha @ no__t-0 | Uma exceção é lançada novamente e a exceção é especificada explicitamente na instrução throw. Se uma exceção for lançada novamente pela especificação da exceção na instrução throw, a lista de chamadas de método entre o método original que lançou a exceção e o método atual será perdida. |
| CA2201 | [CA2201: Não gerar tipos de exceção reservados @ no__t-0 | Isso torna o erro original difícil de detectar e depurar. |
| CA2202 | [CA2202: Não descartar objetos várias vezes @ no__t-0 |Uma implementação do método contém caminhos de código que poderiam causar várias chamadas para System.IDisposable.Dispose ou para um equivalente a Dispose (como um método Close() em alguns tipos) no mesmo objeto. |
| CA2204 | [CA2204: Os literais devem ser escritos corretamente @ no__t-0 | Uma cadeia de caracteres literal em um corpo de método contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft. |
| CA2205 | [CA2205: Usar equivalentes gerenciados da API do Win32 @ no__t-0 | Um método Invoke do sistema operacional é definido e um método .NET que tem a funcionalidade equivalente está disponível. |
| CA2207 | [CA2207: Inicializar campos estáticos do tipo de valor embutido @ no__t-0 | Um tipo de valor declara um construtor estático explícito. Para corrigir uma violação dessa regra, inicialize todos os dados estáticos quando declarados e remova o construtor estático. |
| CA2208 |[CA2208: Instanciar exceções de argumento corretamente @ no__t-0 | For feita uma chamada para o construtor padrão (sem parâmetros) de um tipo de exceção que seja ou derive de ArgumentException, ou um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção que seja ou derive de ArgumentException. |
| CA2210 |[CA2210: Assemblies devem ter nomes fortes válidos @ no__t-0 | O nome forte protege clientes do carregamento desconhecido de um assembly adulterado. Os assemblies sem nomes fortes não devem ser implantados fora de cenários muito limitados. Se você compartilhar ou distribuir assemblies não assinados corretamente, o assembly poderá ser adulterado, o Common Language Runtime poderá não carregar o assembly ou o usuário talvez precise desabilitar a verificação em seu computador. |
| CA2211 |[CA2211: Campos não constantes não devem ser visíveis @ no__t-0 | Os campos estáticos que não são constantes nem somente leitura não são thread-safe. O acesso a esse campo deve ser controlado cuidadosamente e exige técnicas de programação avançadas para sincronizar o acesso ao objeto da classe. |
| CA2212 | [CA2212: Não marcar componentes atendidos com WebMethod @ no__t-0 |Um método em um tipo herdado de System.EnterpriseServices.ServicedComponent é marcado usando-se System.Web.Services.WebMethodAttribute. Como WebMethodAttribute e um método ServicedComponent têm comportamento e requisitos conflitantes para o contexto e o fluxo de transações, o comportamento do método estará incorreto em alguns cenários. |
| CA2213 | [CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md) | Um tipo que implementa System.IDisposable declara campos que são de tipos que também implementam IDisposable. O método Dispose do campo não é chamado pelo método Dispose do tipo declarante. |
| CA2214 | [CA2214: Não chamar métodos substituíveis em construtores @ no__t-0 | Ao chamar um método virtual, o construtor da instância que invoca o método pode não ter sido executado. |
| CA2215 | [CA2215: Métodos Dispose devem chamar a classe base Dispose @ no__t-0 | Se for herdado de um tipo descartável, um tipo deverá chamar o método Dispose do tipo de base em seu próprio método Dispose. |
| CA2216 |[CA2216: Tipos descartáveis devem declarar finalizador @ no__t-0 | Um tipo que implementa System.IDisposable e tem campos que sugerem o uso de recursos não gerenciados não implementa um finalizador, conforme descrito por Object.Finalize. |
| CA2217 | [CA2217: Não marque enums com FlagsAttribute @ no__t-0 |Uma enumeração visível externamente é marcada usando-se FlagsAttribute e tem um ou mais valores que não são potências de dois ou uma combinação dos outros valores definidos na enumeração. |
| CA2218 |[CA2218: Substituir GetHashCode ao substituir é igual a @ no__t-0 | GetHashCode retorna um valor, com base na instância atual, adequado para algoritmos de hash e estruturas de dados como uma tabela de hash. Dois objetos que tenham o mesmo tipo e sejam iguais devem retornar o mesmo código hash. |
| CA2219 | [CA2219: Não gerar exceções nas cláusulas de exceção @ no__t-0 | Quando uma exceção é acionada em uma cláusula finally ou fault, a nova exceção oculta a exceção ativa. Quando uma exceção é acionada em uma cláusula de filtro, o tempo de execução captura silenciosamente a exceção. Isso torna o erro original difícil de detectar e depurar. |
| CA2220 | [CA2220: Os finalizadores devem chamar o finalizador de classe base @ no__t-0 | A finalização deve ser propagada em toda a hierarquia de herança. Para garantir isso, os tipos devem chamar o método Finalize de classe base em seu próprio método Finalize. |
| CA2221 |[CA2221: Os finalizadores devem ser protegidos @ no__t-0 | Os finalizadores deve usar o modificador de acesso da família. |
| CA2222 | [CA2222: Não diminuir a visibilidade de membro herdada @ no__t-0 |Você não deve alterar o modificador de acesso para membros herdados. A alteração de um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método. |
| CA2223 | [CA2223: Os membros devem ser diferentes por mais do que o tipo de retorno @ no__t-0 | Embora o Common Language Runtime permita o uso de tipos de retorno na diferenciação de membros outrora idênticos, este recurso não está na CLS nem é um recurso comum das linguagens de programação do .NET. |
| CA2224 | [CA2224: Substituir Equals no operador de sobrecarga igual a @ no__t-0 | Um tipo público implementa o operador de igualdade, mas não substitui Object.Equals. |
| CA2225 | [CA2225: Sobrecargas de operador têm nomes alternativos @ no__t-0 |Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado. O membro alternativo nomeado fornece acesso à mesma funcionalidade que o operador, e é fornecido para desenvolvedores que programem em linguagens que não dão suporte a operadores sobrecarregados. |
| CA2226 | [CA2226: Os operadores devem ter sobrecargas simétricas @ no__t-0 | Um tipo implementa o operador de igualdade ou de desigualdade e não implementa o operador oposto. |
| CA2227 |[CA2227: As propriedades da coleção devem ser somente leitura @ no__t-0 |Uma propriedade collection gravável permite que um usuário substitua a coleção por uma coleção diferente. Uma propriedade somente leitura evita que a coleção seja substituída, mas ainda permite que membros individuais sejam definidos. |
| CA2228 | [CA2228: Não enviar formatos de recurso não lançados @ no__t-0 | Os arquivos de recursos criados usando versões de pré-lançamento do .NET podem não ser utilizáveis por versões do .NET com suporte. |
| CA2229 | [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md) | Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido. |
| CA2230 | [CA2230: Usar params para argumentos de variável @ no__t-0 | Um tipo público ou protegido contém um método público ou protegido que usa a convenção de chamada VarArgs, em vez da palavra-chave params. |
| CA2231 | [CA2231: o operador de sobrecarga é igual ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Um tipo de valor substitui Object.Equals, mas não implementa o operador de igualdade. |
| CA2232 | [CA2232: Marcar pontos de entrada de Windows Forms com STAThread @ no__t-0 | STAThreadAttribute indica que o modelo de threading COM para o aplicativo é um single-threaded apartment. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente. |
| CA2233 |[CA2233: As operações não devem exceder o estouro de @ no__t-0 | Você não deve realizar operações aritméticas sem primeiro validar os operandos. Isso garante que o resultado da operação não esteja fora do intervalo de valores possíveis para os tipos de dados que estão envolvidos. |
| CA2234 | [CA2234: Passe objetos System. Uri em vez de cadeias de caracteres @ no__t-0 | Foi feita uma chamada para um método com um parâmetro de cadeia de caracteres cujo nome contém "uri", "URI", "urn", "URN", "url" ou "URL". O tipo declarante do método contém uma sobrecarga do método correspondente que possui um parâmetro System.Uri. |
| CA2235 | [CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md) | Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável. |
| CA2236 | [CA2236: Chamar métodos de classe base em tipos ISerializable @ no__t-0 | Para corrigir uma violação dessa regra, chame o método GetObjectData de tipo base ou o construtor de serialização do método de tipo derivado correspondente ou do construtor. |
| CA2237 | [CA2237: Marcar tipos ISerializable com SerializableAttribute @ no__t-0 | Para serem reconhecidos pelo Common Language Runtime como serializáveis, os tipos devem ser marcados usando-se o atributo SerializableAttribute, mesmo quando o tipo usa uma rotina de serialização personalizada por meio da implementação da interface ISerializable. |
| CA2238 |[CA2238: Implementar métodos de serialização corretamente @ no__t-0 | Um método que trata um evento de serialização não tem a assinatura, o tipo de retorno ou a visibilidade corretos. |
| CA2239 | [CA2239: Fornecer métodos de desserialização para campos opcionais @ no__t-0 | Um tipo tem um campo que foi marcado usando-se o atributo System.Runtime.Serialization.OptionalFieldAttribute, e o tipo não fornece métodos de tratamento de eventos de desserialização. |
| CA2240 | [CA2240: Implementar ISerializable corretamente @ no__t-0 | Para corrigir uma violação dessa regra, deixe o método GetObjectData visível e substituível e verifique se todos os campos de instância estão incluídos no processo de serialização ou marcados explicitamente usando-se o atributo NonSerializedAttribute. |
| CA2241 | [CA2241: Forneça os argumentos corretos para os métodos de formatação @ no__t-0 | O argumento format passado para System.String.Format não contém um item de formato correspondente a cada argumento do objeto ou vice-versa. |
| CA2242 |[CA2242: Testar para NaN corretamente @ no__t-0 | Essa expressão testa um valor em Single.Nan ou Double.Nan. Use Single.IsNan (único) ou Double.IsNan (duplo) para testar o valor. |
| CA2243 |[CA2243: Literais de cadeia de caracteres de atributo devem ser analisados corretamente @ no__t-0 | O parâmetro literal da cadeia de caracteres de um atributo não é analisado corretamente para uma URL, um GUID ou uma versão. |
| CA5122 | [CA5122: as declarações de P-Invoke não devem ser críticas para segurança](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | Os métodos são marcados como SecuritySafeCritical quando executam uma operação confidencial de segurança, mas também são seguros para serem usados pelo código transparente. O código transparente jamais pode chamar diretamente o código nativo por meio de um P/Invoke. Por isso, a marcação de um P/Invoke como crítico de segurança não permitirá que o código transparente o chame, e é enganosa na análise de segurança. |
