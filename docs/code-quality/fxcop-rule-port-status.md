---
title: Status da porta de regra do FxCop
ms.date: 05/21/2019
description: Saiba mais sobre as regras de análise de código estático que foram modeladas para os analisadores do .NET no Visual Studio. Exiba regras e recursos portados sobre atualizações de porta.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: de23f3529cfcd321b0a7c3f9844ac69d96fed9c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860315"
---
# <a name="fxcop-rule-port-status"></a>Status da porta de regra do FxCop

Se você usou anteriormente a análise de código estático no Visual Studio, talvez esteja imaginando quais dessas regras estão disponíveis na implementação atual como [analisadores .net](install-net-analyzers.md). Esta página lista as regras que foram portadas. Veja [regras não portadas](fxcop-unported-rules.md) para aqueles que não foram portados e se há planos para portá-los.

## <a name="ported-rules"></a>Regras portadas

A [página de documentação gerada automaticamente](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) no repositório Roslyn-Analyzers tem a lista mais atualizada de regras que foram modeladas para os analisadores do Roslyn. Essa página também tem informações adicionais, como se a regra está habilitada por padrão e se tem uma correção de *código* associada. (As[correções de código](../ide/quick-actions.md) são correções de um único clique disponíveis no menu de ícones de lâmpada no Visual Studio.)

A partir da data desta página, a lista de regras do FxCop que foram modeladas para os [analisadores .net](install-net-analyzers.md) inclui:

ID da regra | Title
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Não declarar membros estáticos em tipos genéricos
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Tipos com campos descartáveis devem ser descartáveis
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Não expor listas genéricas
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Usar instâncias do manipulador de eventos genérico
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Evitar parâmetros excessivos em tipos genéricos
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Enumerações devem ter valor zero
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Coleções devem implementar uma interface genérica
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Tipos abstratos não devem ter construtores
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Marcar assemblies com CLSCompliant
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Marcar assemblies com a versão do assembly
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Marcar assemblies com ComVisible
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Marcar atributos com AttributeUsageAttribute
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Definir acessadores para argumentos de atributo
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | Evitar parâmetros out
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Usar propriedades quando apropriado
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Marcar enumerações com FlagsAttribute
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | O armazenamento de enumeração deve ser Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Usar eventos quando apropriado
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Não capturar tipos de exceção geral
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Implementar construtores de exceção padrão
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Métodos de interface devem ser chamados por tipos filho
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | Tipos aninhados não devem ser visíveis
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Substituir métodos em tipos comparáveis
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Evitar interfaces vazias
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | Fornecer a mensagem ObsoleteAttribute
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Usar argumento integral ou de cadeia de caracteres para indexadores
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Propriedades não devem ser somente gravação
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Não passar tipos por referência
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Não sobrecarregar o operador equals em tipos de referência
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Não declarar membros protegidos em tipos selados
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Declarar tipos em namespaces
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Não declarar campos de instância visíveis
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Tipos de detentor estáticos devem ser estáticos ou não herdáveis
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Tipos de detentor estáticos não devem ter construtores (CA1053 é parte de [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) para analisadores .net)
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Parâmetros de URI não devem ser cadeias de caracteres
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Os valores de retorno de URI não devem ser cadeias de caracteres
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | As propriedades de URI não devem ser cadeias de caracteres
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Tipos não devem estender determinados tipos base
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Mover PInvokes para classe de métodos nativos
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Não ocultar métodos de classe base
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Validar argumentos de métodos públicos
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Implementar IDisposable corretamente
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Exceções devem ser públicas
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Não acionar exceções em locais inesperados
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | O tipo {0} deve implementar IEquatable \<T> porque ele substitui Equals
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Substituir Object. Equals (Object) ao implementar IEquatable\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Não passar literais como parâmetros localizados
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | Especificar CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | Especificar IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Especificar StringComparison para fins de clareza
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Normalizar cadeias de caracteres em maiúsculas
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Usar comparação de cadeia de caracteres ordinal
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | P/Invokes não devem ser visíveis
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Evitar herança excessiva
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Evitar complexidade excessiva
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Evitar código de difícil manutenção
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Evitar acoplamento de classes excessivo
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Não nomear valores de enumeração 'Reserved'
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Identificadores não devem conter sublinhados
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Identificadores devem ter um sufixo correto
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Identificadores não devem ter um sufixo incorreto
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | Não prefixar valores de enumeração com um nome de tipo
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Eventos não devem ter o prefixo anterior ou posterior
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Enumerações de sinalizador devem ter nomes no plural
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Identificadores devem ter um prefixo correto
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Identificadores não devem corresponder a palavras-chave
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Apenas enumerações FlagsAttribute devem ter nomes no plural
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | O identificador contém o nome do tipo
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Nomes de propriedades não devem corresponder a métodos get
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Nomes de tipos não devem corresponder a namespaces
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Nomes de parâmetros devem corresponder à declaração base
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Examinar parâmetros não utilizados
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Usar literais quando apropriado
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Não inicializar desnecessariamente
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | Não ignorar resultados do método
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Inicializar campos estáticos de tipo de referência em linha
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Evitar classes internas sem instâncias
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Evitar atributos não selados
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Preferir matrizes denteadas a matrizes multidimensionais
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Substituir equals e o operador equals em tipos de valor
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Os métodos Dispose devem chamar SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Propriedades não devem retornar matrizes
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Remover finalizadores vazios
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Marcar membros como estáticos
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Evitar campos particulares não utilizados
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Marque assemblies com NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Evite as alocações de matriz de comprimento zero.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Descartar objetos antes de perder o escopo
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Não bloquear objetos com identidade fraca
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | Examinar consultas SQL em busca de vulnerabilidades de segurança
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Especificar marshaling para argumentos de cadeias de caracteres P/Invoke
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Examinar manipuladores de eventos visíveis
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Selar métodos que atendem a interfaces particulares
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Não capturar exceções de estado corrompidas
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Relançar para preservar os detalhes da pilha.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Não acionar tipos de exceção reservados
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Inicializar campos estáticos de tipo de valor em linha
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Criar instância de exceções de argumento corretamente
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Campos não constantes não devem ser visíveis
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Campos descartáveis devem ser descartados
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | Não chamar métodos substituíveis em construtores
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Métodos Dispose devem chamar o descarte da classe base
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Tipos descartáveis devem declarar o finalizador
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Não marcar enumerações com FlagsAttribute
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Não gerar exceções em cláusulas finally
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Sobrecargas de operador têm alternativas nomeadas
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Operadores devem ter sobrecargas simétricas
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Propriedades de coleção devem ser somente leitura
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Implementar construtores de serialização
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Sobrecarga do operador Equals no tipo de valor de substituição é igual a
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Passar objetos URI do sistema em vez de cadeias de caracteres
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Marcar todos os campos não serializáveis
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | Marcar tipos ISerializable com serializável
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Fornecer argumentos corretos para métodos de formatação
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Testar para NaN corretamente
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Literais de cadeias de caracteres de atributo devem ser analisados corretamente
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | Não usar o desserializador BinaryFormatter não seguro
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | Não chamar BinaryFormatter.Deserialize sem antes definir BinaryFormatter.Binder
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Verificar se o BinaryFormatter.Binder está definido antes de chamar BinaryFormatter.Deserialize
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | Não usar o desserializador inseguro LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | Não usar o desserializador inseguro NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | Não desserializar sem definir primeiro NetDataContractSerializer.Binder
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Verificar se NetDataContractSerializer.Binder foi definido antes de desserializar
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | Não usar o desserializador inseguro ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | Não desserializar com JavaScriptSerializer usando um SimpleTypeResolver
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Garantir que o JavaScriptSerializer não seja inicializado com SimpleTypeResolver antes de desserializar
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Examinar código quanto a vulnerabilidades de injeção de SQL
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Examinar código quanto a vulnerabilidades de XSS
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Examinar código quanto a vulnerabilidades de injeção de caminho
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Examinar código quanto a vulnerabilidades de divulgação de informações
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Examinar código quanto a vulnerabilidades de injeção de LDAP
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Examinar código quanto a vulnerabilidades de injeção de comando de processo
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Examinar código quanto a vulnerabilidades de redirecionamento aberto
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Examinar código quanto a vulnerabilidades de injeção de XPath
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Examinar código quanto a vulnerabilidades de injeção de XML
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Examinar código quanto a vulnerabilidades de injeção de XAML
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Examinar código quanto a vulnerabilidades de injeção de DLL
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Examinar código quanto a vulnerabilidades de injeção de regex
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | Não adicionar esquema por URL
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Processamento DTD não seguro em XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Processamento de script XSLT inseguro.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Processamento inseguro em design de API, XmlDocument e XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Marcar manipuladores de verbo com o token de antifalsificação de validação
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | Não usar algoritmos de criptografia fracos
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Não usar algoritmos de criptografia desfeitos
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Não usar modos de criptografia não seguros
CA5359 | Não desabilitar a validação de certificado
CA5360 | Não chamar métodos perigosos na desserialização
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Não desabilitar o uso do SChannel de criptografia forte
CA5362 | Não se referir à classe serializável Self
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | Não desabilitar a validação de solicitação
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Não usar protocolos de segurança preteridos
CA5365 | Não desabilitar a verificação de cabeçalho HTTP
CA5366 | Usar XmlReader para XML de leitura de DataSet
CA5367 | Não serializar tipos com campos de ponteiro
CA5368 | Definir ViewStateUserKey para classes derivadas da página
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Usar XmlReader para desserializar
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Usar XmlReader para validar o leitor
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Usar XmlReader para leitura de esquema
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | Usar XmlReader para XPathDocument
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Não usar a função de derivação de chave obsoleta
CA5374 | Não usar XslTransform
CA5375 | Não usar assinatura de acesso compartilhado da conta
CA5376 | Usar SharedAccessProtocol HttpsOnly
CA5377 | Usar política de acesso no nível do contêiner
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | Não desabilite ServicePointManagerSecurityProtocols
CA5379 | Não usar algoritmo de função de derivação de chave fraca
CA9999 | Incompatibilidade de versão do analisador

## <a name="see-also"></a>Consulte também

- [Regras do analisador .NET](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
