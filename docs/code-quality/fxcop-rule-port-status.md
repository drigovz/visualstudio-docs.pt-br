---
title: Status da porta de regra do FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508360"
---
# <a name="fxcop-rule-port-status"></a>Status da porta de regra do FxCop

Se você usou anteriormente a análise de código estático no Visual Studio, talvez esteja imaginando quais dessas regras estão disponíveis na implementação atual como [analisadores do FxCop](install-fxcop-analyzers.md). Esta página lista as regras que foram portadas. Veja [regras não portadas](fxcop-unported-rules.md) para aqueles que não foram portados e se há planos para portá-los.

## <a name="ported-rules"></a>Regras portadas

A [página de documentação gerada automaticamente](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) no repositório Roslyn-Analyzers tem a lista mais atualizada de regras que foram modeladas para analisadores do FxCop. Essa página também tem informações adicionais, como se a regra está habilitada por padrão e se tem uma correção de *código*associada. (As[correções de código](../ide/quick-actions.md) são correções de um único clique disponíveis no menu de ícones de lâmpada no Visual Studio.)

A partir da data desta página, a lista de regras do FxCop que foram modeladas para [analisadores de FxCop](install-fxcop-analyzers.md) inclui:

ID da regra | Title
--------|---------
[CA1000](ca1000.md) | Não declarar membros estáticos em tipos genéricos
[CA1001](ca1001.md) | Tipos com campos descartáveis devem ser descartáveis
[CA1002](ca1002.md) | Não expor listas genéricas
[CA1003](ca1003.md) | Usar instâncias do manipulador de eventos genérico
[CA1005](ca1005.md) | Evitar parâmetros excessivos em tipos genéricos
[CA1008](ca1008.md) | Enumerações devem ter valor zero
[CA1010](ca1010.md) | Coleções devem implementar uma interface genérica
[CA1012](ca1012.md) | Tipos abstratos não devem ter construtores
[CA1014](ca1014.md) | Marcar assemblies com CLSCompliant
[CA1016](ca1016.md) | Marcar assemblies com a versão do assembly
[CA1017](ca1017.md) | Marcar assemblies com ComVisible
[CA1018](ca1018.md) | Marcar atributos com AttributeUsageAttribute
[CA1019](ca1019.md) | Definir acessadores para argumentos de atributo
[CA1021](ca1021.md) | Evitar parâmetros out
[CA1024](ca1024.md) | Usar propriedades quando apropriado
[CA1027](ca1027.md) | Marcar enumerações com FlagsAttribute
[CA1028](ca1028.md) | O armazenamento de enumeração deve ser Int32
[CA1030](ca1030.md) | Usar eventos quando apropriado
[CA1031](ca1031.md) | Não capturar tipos de exceção geral
[CA1032](ca1032.md) | Implementar construtores de exceção padrão
[CA1033](ca1033.md) | Métodos de interface devem ser chamados por tipos filho
[CA1034](ca1034.md) | Tipos aninhados não devem ser visíveis
[CA1036](ca1036.md) | Substituir métodos em tipos comparáveis
[CA1040](ca1040.md) | Evitar interfaces vazias
[CA1041](ca1041.md) | Fornecer a mensagem ObsoleteAttribute
[CA1043](ca1043.md) | Usar argumento integral ou de cadeia de caracteres para indexadores
[CA1044](ca1044.md) | Propriedades não devem ser somente gravação
[CA1045](ca1045.md) | Não passar tipos por referência
[CA1046](ca1046.md) | Não sobrecarregar o operador equals em tipos de referência
[CA1047](ca1047.md) | Não declarar membros protegidos em tipos selados
[CA1050](ca1050.md) | Declarar tipos em namespaces
[CA1051](ca1051.md) | Não declarar campos de instância visíveis
[CA1052](ca1052.md) | Tipos de detentor estáticos devem ser estáticos ou não herdáveis
[CA1053](ca1053.md) | Tipos de detentor estáticos não devem ter construtores (CA1053 é parte de [CA1052](ca1052.md) para analisadores de FxCop)
[CA1054](ca1054.md) | Parâmetros de URI não devem ser cadeias de caracteres
[CA1055](ca1055.md) | Os valores de retorno de URI não devem ser cadeias de caracteres
[CA1056](ca1056.md) | As propriedades de URI não devem ser cadeias de caracteres
[CA1058](ca1058.md) | Tipos não devem estender determinados tipos base
[CA1060](ca1060.md) | Mover PInvokes para classe de métodos nativos
[CA1061](ca1061.md) | Não ocultar métodos de classe base
[CA1062](ca1062.md) | Validar argumentos de métodos públicos
[CA1063](ca1063.md) | Implementar IDisposable corretamente
[CA1064](ca1064.md) | Exceções devem ser públicas
[CA1065](ca1065.md) | Não acionar exceções em locais inesperados
[CA1066](ca1066.md) | O tipo {0} deve implementar IEquatable \<T> porque ele substitui Equals
[CA1067](ca1067.md) | Substituir Object. Equals (Object) ao implementar IEquatable\<T>
[CA1303](ca1303.md) | Não passar literais como parâmetros localizados
[CA1304](ca1304.md) | Especificar CultureInfo
[CA1305](ca1305.md) | Especificar IFormatProvider
[CA1307](ca1307.md) | Especificar StringComparison para fins de clareza
[CA1308](ca1308.md) | Normalizar cadeias de caracteres em maiúsculas
[CA1309](ca1309.md) | Usar comparação de cadeia de caracteres ordinal
[CA1401](ca1401.md) | P/Invokes não devem ser visíveis
[CA1501](ca1501.md) | Evitar herança excessiva
[CA1502](ca1502.md) | Evitar complexidade excessiva
[CA1505](ca1505.md) | Evitar código de difícil manutenção
[CA1506](ca1506.md) | Evitar acoplamento de classes excessivo
[CA1700](ca1700.md) | Não nomear valores de enumeração 'Reserved'
[CA1707](ca1707.md) | Identificadores não devem conter sublinhados
[CA1708](ca1708.md) | Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas
[CA1710](ca1710.md) | Identificadores devem ter um sufixo correto
[CA1711](ca1711.md) | Identificadores não devem ter um sufixo incorreto
[CA1712](ca1712.md) | Não prefixar valores de enumeração com um nome de tipo
[CA1713](ca1713.md) | Eventos não devem ter o prefixo anterior ou posterior
[CA1714](ca1714.md) | Enumerações de sinalizador devem ter nomes no plural
[CA1715](ca1715.md) | Identificadores devem ter um prefixo correto
[CA1716](ca1716.md) | Identificadores não devem corresponder a palavras-chave
[CA1717](ca1717.md) | Apenas enumerações FlagsAttribute devem ter nomes no plural
[CA1720](ca1720.md) | O identificador contém o nome do tipo
[CA1721](ca1721.md) | Nomes de propriedades não devem corresponder a métodos get
[CA1724](ca1724.md) | Nomes de tipos não devem corresponder a namespaces
[CA1725](ca1725.md) | Nomes de parâmetros devem corresponder à declaração base
[CA1801](ca1801.md) | Examinar parâmetros não utilizados
[CA1802](ca1802.md) | Usar literais quando apropriado
[CA1805](ca1805.md) | Não inicializar desnecessariamente
[CA1806](ca1806.md) | Não ignorar resultados do método
[CA1810](ca1810.md) | Inicializar campos estáticos de tipo de referência em linha
[CA1812](ca1812.md) | Evitar classes internas sem instâncias
[CA1813](ca1813.md) | Evitar atributos não selados
[CA1814](ca1814.md) | Preferir matrizes denteadas a matrizes multidimensionais
[CA1815](ca1815.md) | Substituir equals e o operador equals em tipos de valor
[CA1816](ca1816.md) | Os métodos Dispose devem chamar SuppressFinalize
[CA1819](ca1819.md) | Propriedades não devem retornar matrizes
[CA1820](ca1820.md) | Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres
[CA1821](ca1821.md) | Remover finalizadores vazios
[CA1822](ca1822.md) | Marcar membros como estáticos
[CA1823](ca1823.md) | Evitar campos particulares não utilizados
[CA1824](ca1824.md) | Marque assemblies com NeutralResourcesLanguageAttribute
[CA1825](ca1825.md) | Evite as alocações de matriz de comprimento zero.
[CA2000](ca2000.md) | Descartar objetos antes de perder o escopo
[CA2002](ca2002.md) | Não bloquear objetos com identidade fraca
[CA2100](ca2100.md) | Examinar consultas SQL em busca de vulnerabilidades de segurança
[CA2101](ca2101.md) | Especificar marshaling para argumentos de cadeias de caracteres P/Invoke
[CA2109](ca2109.md) | Examinar manipuladores de eventos visíveis
[CA2119](ca2119.md) | Selar métodos que atendem a interfaces particulares
[CA2153](ca2153.md) | Não capturar exceções de estado corrompidas
[CA2200](ca2200.md) | Relançar para preservar os detalhes da pilha.
[CA2201](ca2201.md) | Não acionar tipos de exceção reservados
[CA2207](ca2207.md) | Inicializar campos estáticos de tipo de valor em linha
[CA2208](ca2208.md) | Criar instância de exceções de argumento corretamente
[CA2211](ca2211.md) | Campos não constantes não devem ser visíveis
[CA2213](ca2213.md) | Campos descartáveis devem ser descartados
[CA2214](ca2214.md) | Não chamar métodos substituíveis em construtores
[CA2215](ca2215.md) | Métodos Dispose devem chamar o descarte da classe base
[CA2216](ca2216.md) | Tipos descartáveis devem declarar o finalizador
[CA2217](ca2217.md) | Não marcar enumerações com FlagsAttribute
[CA2219](ca2219.md) | Não gerar exceções em cláusulas finally
[CA2225](ca2225.md) | Sobrecargas de operador têm alternativas nomeadas
[CA2226](ca2226.md) | Operadores devem ter sobrecargas simétricas
[CA2227](ca2227.md) | Propriedades de coleção devem ser somente leitura
[CA2229](ca2229.md) | Implementar construtores de serialização
[CA2231](ca2231.md) | Sobrecarga do operador Equals no tipo de valor de substituição é igual a
[CA2234](ca2234.md) | Passar objetos URI do sistema em vez de cadeias de caracteres
[CA2235](ca2235.md) | Marcar todos os campos não serializáveis
[CA2237](ca2237.md) | Marcar tipos ISerializable com serializável
[CA2241](ca2241.md) | Fornecer argumentos corretos para métodos de formatação
[CA2242](ca2242.md) | Testar para NaN corretamente
[CA2243](ca2243.md) | Literais de cadeias de caracteres de atributo devem ser analisados corretamente
[CA2300](ca2300.md) | Não usar o desserializador BinaryFormatter não seguro
[CA2301](ca2301.md) | Não chamar BinaryFormatter.Deserialize sem antes definir BinaryFormatter.Binder
[CA2302](ca2302.md) | Verificar se o BinaryFormatter.Binder está definido antes de chamar BinaryFormatter.Deserialize
[CA2305](ca2305.md) | Não usar o desserializador inseguro LosFormatter
[CA2310](ca2310.md) | Não usar o desserializador inseguro NetDataContractSerializer
[CA2311](ca2311.md) | Não desserializar sem definir primeiro NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Verificar se NetDataContractSerializer.Binder foi definido antes de desserializar
[CA2315](ca2315.md) | Não usar o desserializador inseguro ObjectStateFormatter
[CA2321](ca2321.md) | Não desserializar com JavaScriptSerializer usando um SimpleTypeResolver
[CA2322](ca2322.md) | Garantir que o JavaScriptSerializer não seja inicializado com SimpleTypeResolver antes de desserializar
[CA3001](ca3001.md) | Examinar código quanto a vulnerabilidades de injeção de SQL
[CA3002](ca3002.md) | Examinar código quanto a vulnerabilidades de XSS
[CA3003](ca3003.md) | Examinar código quanto a vulnerabilidades de injeção de caminho
[CA3004](ca3004.md) | Examinar código quanto a vulnerabilidades de divulgação de informações
[CA3005](ca3005.md) | Examinar código quanto a vulnerabilidades de injeção de LDAP
[CA3006](ca3006.md) | Examinar código quanto a vulnerabilidades de injeção de comando de processo
[CA3007](ca3007.md) | Examinar código quanto a vulnerabilidades de redirecionamento aberto
[CA3008](ca3008.md) | Examinar código quanto a vulnerabilidades de injeção de XPath
[CA3009](ca3009.md) | Examinar código quanto a vulnerabilidades de injeção de XML
[CA3010](ca3010.md) | Examinar código quanto a vulnerabilidades de injeção de XAML
[CA3011](ca3011.md) | Examinar código quanto a vulnerabilidades de injeção de DLL
[CA3012](ca3012.md) | Examinar código quanto a vulnerabilidades de injeção de regex
[CA3061](ca3061.md) | Não adicionar esquema por URL
[CA3075](ca3075.md) | Processamento DTD não seguro em XML
[CA3076](ca3076.md) | Processamento de script XSLT inseguro.
[CA3077](ca3077.md) | Processamento inseguro em design de API, XmlDocument e XmlTextReader
[CA3147](ca3147.md) | Marcar manipuladores de verbo com o token de antifalsificação de validação
[CA5350](ca5350.md) | Não usar algoritmos de criptografia fracos
[CA5351](ca5351.md) | Não usar algoritmos de criptografia desfeitos
[CA5358](ca5358.md) | Não usar modos de criptografia não seguros
CA5359 | Não desabilitar a validação de certificado
CA5360 | Não chamar métodos perigosos na desserialização
[CA5361](ca5361.md) | Não desabilitar o uso do SChannel de criptografia forte
CA5362 | Não se referir à classe serializável Self
[CA5363](ca5363.md) | Não desabilitar a validação de solicitação
[CA5364](ca5364.md) | Não usar protocolos de segurança preteridos
CA5365 | Não desabilitar a verificação de cabeçalho HTTP
CA5366 | Usar XmlReader para XML de leitura de DataSet
CA5367 | Não serializar tipos com campos de ponteiro
CA5368 | Definir ViewStateUserKey para classes derivadas da página
[CA5369](ca5369.md) | Usar XmlReader para desserializar
[CA5370](ca5370.md) | Usar XmlReader para validar o leitor
[CA5371](ca5371.md) | Usar XmlReader para leitura de esquema
[CA5372](ca5372.md) | Usar XmlReader para XPathDocument
[CA5373](ca5373.md) | Não usar a função de derivação de chave obsoleta
CA5374 | Não usar XslTransform
CA5375 | Não usar assinatura de acesso compartilhado da conta
CA5376 | Usar SharedAccessProtocol HttpsOnly
CA5377 | Usar política de acesso no nível do contêiner
[CA5378](ca5378.md) | Não desabilite ServicePointManagerSecurityProtocols
CA5379 | Não usar algoritmo de função de derivação de chave fraca
CA9999 | Incompatibilidade de versão do analisador

## <a name="see-also"></a>Confira também

- [Regras Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
