---
title: Status da porta de regra do FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2e635f2cbbeda67c4fbed760eb7e57dfcf140d15
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604873"
---
# <a name="fxcop-rule-port-status"></a>Status da porta de regra do FxCop

Se você usou anteriormente a análise de código estático em uma versão anterior do Visual Studio, talvez esteja imaginando quais dessas regras estão disponíveis na implementação atual como analisadores do [FxCop](install-fxcop-analyzers.md). Esta página lista as regras que são portadas, bem como aquelas que não foram portadas e se há planos para portá-las.

## <a name="ported-rules"></a>Regras portadas

A [página de documentação gerada automaticamente](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) no repositório Roslyn-Analyzers tem a lista mais atualizada de regras que foram modeladas para analisadores do FxCop. Essa página também tem informações adicionais, como se a regra está habilitada por padrão e se tem uma correção de *código*associada. (As correções de[código](../ide/quick-actions.md) são correções de um único clique disponíveis no menu de ícones de lâmpada no Visual Studio.)

A partir da data desta página, a lista de regras do FxCop que foram modeladas para [analisadores de FxCop](install-fxcop-analyzers.md) inclui:

ID da regra | Título
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Não declarar membros estáticos em tipos genéricos
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Tipos com campos descartáveis devem ser descartáveis
[CA1003](ca1003-use-generic-event-handler-instances.md) | Usar instâncias do manipulador de eventos genérico
[CA1008](ca1008-enums-should-have-zero-value.md) | Enumerações devem ter valor zero
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Coleções devem implementar uma interface genérica
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Tipos abstratos não devem ter construtores
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Marcar assemblies com CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Marcar assemblies com a versão do assembly
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Marcar assemblies com ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Marcar atributos com AttributeUsageAttribute
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Definir acessadores para argumentos de atributo
[CA1024](ca1024-use-properties-where-appropriate.md) | Usar propriedades quando apropriado
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Marcar enumerações com FlagsAttribute
[CA1028](ca1028-enum-storage-should-be-int32.md) | O armazenamento de enumeração deve ser Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Usar eventos quando apropriado
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Não capturar tipos de exceção geral
[CA1032](ca1032-implement-standard-exception-constructors.md) | Implementar construtores de exceção padrão
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Métodos de interface devem ser chamados por tipos filho
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Tipos aninhados não devem ser visíveis
[CA1036](ca1036-override-methods-on-comparable-types.md) | Substituir métodos em tipos comparáveis
[CA1040](ca1040-avoid-empty-interfaces.md) | Evitar interfaces vazias
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Fornecer a mensagem ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Usar argumento integral ou de cadeia de caracteres para indexadores
[CA1044](ca1044-properties-should-not-be-write-only.md) | Propriedades não devem ser somente gravação
[CA1050](ca1050-declare-types-in-namespaces.md) | Declarar tipos em namespaces
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Não declarar campos de instância visíveis
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Tipos de detentor estáticos devem ser estáticos ou não herdáveis
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Tipos de detentor estáticos não devem ter construtores (CA1053 é parte de [CA1052](ca1052-static-holder-types-should-be-sealed.md) para analisadores de FxCop)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Parâmetros de URI não devem ser cadeias de caracteres
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Os valores de retorno de URI não devem ser cadeias de caracteres
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | As propriedades de URI não devem ser cadeias de caracteres
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Tipos não devem estender determinados tipos base
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Mover PInvokes para classe de métodos nativos
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Não ocultar métodos de classe base
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Validar argumentos de métodos públicos
[CA1063](ca1063-implement-idisposable-correctly.md) | Implementar IDisposable corretamente
[CA1064](ca1064-exceptions-should-be-public.md) | Exceções devem ser públicas
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Não acionar exceções em locais inesperados
CA1066 | O {0} tipo deve implementar\<IEquatable T > porque ele substitui Equals
CA1067 | Substituir Object. Equals (Object) ao implementar\<IEquatable T >
CA1068 | Os parâmetros de CancellationToken devem vir por último
CA1200 | Evite usar marcas cref com um prefixo
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Não passar literais como parâmetros localizados
[CA1304](ca1304-specify-cultureinfo.md) | Especificar CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Especificar IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Especificar StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normalizar cadeias de caracteres em maiúsculas
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Usar comparação de cadeia de caracteres ordinal
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | P/Invokes não devem ser visíveis
[CA1501](ca1501-avoid-excessive-inheritance.md) | Evitar herança excessiva
[CA1502](ca1502-avoid-excessive-complexity.md) | Evitar complexidade excessiva
[CA1505](ca1505-avoid-unmaintainable-code.md) | Evitar código de difícil manutenção
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Evitar acoplamento de classes excessivo
[CA1507](ca1507.md) | Usar nameof para expressar nomes de símbolo
CA1508 | Evitar código condicional inativo
CA1509 | Entrada inválida no arquivo de especificação de regra de métricas de código
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Identificadores não devem conter sublinhados
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Identificadores devem ter um sufixo correto
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Identificadores não devem ter um sufixo incorreto
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | Não prefixar valores de enumeração com um nome de tipo
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Enumerações de sinalizador devem ter nomes no plural
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Identificadores devem ter um prefixo correto
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Identificadores não devem corresponder a palavras-chave
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Apenas enumerações FlagsAttribute devem ter nomes no plural
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | O identificador contém o nome do tipo
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Nomes de propriedades não devem corresponder a métodos get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Nomes de tipos não devem corresponder a namespaces
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Nomes de parâmetros devem corresponder à declaração base
[CA1801](ca1801-review-unused-parameters.md) | Examinar parâmetros não utilizados
[CA1802](ca1802-use-literals-where-appropriate.md) | Usar literais quando apropriado
[CA1806](ca1806-do-not-ignore-method-results.md) | Não ignorar resultados do método
[CA1810](ca1810-initialize-reference-type-static-fields-inline.md) | Inicializar campos estáticos de tipo de referência em linha
[CA1812](ca1812-avoid-uninstantiated-internal-classes.md) | Evitar classes internas sem instâncias
[CA1813](ca1813-avoid-unsealed-attributes.md) | Evitar atributos não selados
[CA1814](ca1814-prefer-jagged-arrays-over-multidimensional.md) | Preferir matrizes denteadas a matrizes multidimensionais
[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md) | Substituir equals e o operador equals em tipos de valor
[CA1816](ca1816-call-gc-suppressfinalize-correctly.md) | Os métodos Dispose devem chamar SuppressFinalize
[CA1819](ca1819-properties-should-not-return-arrays.md) | Propriedades não devem retornar matrizes
[CA1820](ca1820-test-for-empty-strings-using-string-length.md) | Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres
[CA1821](ca1821-remove-empty-finalizers.md) | Remover finalizadores vazios
[CA1822](ca1822-mark-members-as-static.md) | Marcar membros como estáticos
[CA1823](ca1823-avoid-unused-private-fields.md) | Evitar campos particulares não utilizados
[CA1824](ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Marque assemblies com NeutralResourcesLanguageAttribute
CA1825 | Evite as alocações de matriz de comprimento zero.
CA1826 | Não use métodos enumeráveis em coleções indexáveis. Em vez disso, use a coleção diretamente
[CA2000](ca2000-dispose-objects-before-losing-scope.md) | Descartar objetos antes de perder o escopo
[CA2002](ca2002-do-not-lock-on-objects-with-weak-identity.md) | Não bloquear objetos com identidade fraca
[CA2007](ca2007-do-not-directly-await-task.md) | Considere chamar ConfigureAwait na tarefa esperada
CA2008 | Não criar tarefas sem passar um TaskScheduler
CA2009 | Não chamar ToImmutableCollection em um valor imutável
CA2010 | Sempre consumir o valor retornado pelos métodos marcados com PreserveSigAttribute
[CA2100](ca2100-review-sql-queries-for-security-vulnerabilities.md) | Examinar consultas SQL em busca de vulnerabilidades de segurança
[CA2101](ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | Especificar marshaling para argumentos de cadeias de caracteres P/Invoke
[CA2119](ca2119-seal-methods-that-satisfy-private-interfaces.md) | Selar métodos que atendem a interfaces particulares
[CA2153](ca2153-avoid-handling-corrupted-state-exceptions.md) | Não capturar exceções de estado corrompidas
[CA2200](ca2200-rethrow-to-preserve-stack-details.md) | Relançar para preservar os detalhes da pilha.
[CA2201](ca2201-do-not-raise-reserved-exception-types.md) | Não acionar tipos de exceção reservados
[CA2207](ca2207-initialize-value-type-static-fields-inline.md) | Inicializar campos estáticos de tipo de valor em linha
[CA2208](ca2208-instantiate-argument-exceptions-correctly.md) | Criar instância de exceções de argumento corretamente
[CA2211](ca2211-non-constant-fields-should-not-be-visible.md) | Campos não constantes não devem ser visíveis
[CA2213](ca2213-disposable-fields-should-be-disposed.md) | Campos descartáveis devem ser descartados
[CA2214](ca2214-do-not-call-overridable-methods-in-constructors.md) | Não chamar métodos substituíveis em construtores
[CA2216](ca2216-disposable-types-should-declare-finalizer.md) | Tipos descartáveis devem declarar o finalizador
[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md) | Não marcar enumerações com FlagsAttribute
[CA2218](ca2218-override-gethashcode-on-overriding-equals.md) | Substituir GetHashCode ao substituir Equals
[CA2219](ca2219-do-not-raise-exceptions-in-exception-clauses.md) | Não gerar exceções em cláusulas finally
[CA2224](ca2224-override-equals-on-overloading-operator-equals.md) | Substituir Equals no operador de sobrecarga igual a
[CA2225](ca2225-operator-overloads-have-named-alternates.md) | Sobrecargas de operador têm alternativas nomeadas
[CA2226](ca2226-operators-should-have-symmetrical-overloads.md) | Operadores devem ter sobrecargas simétricas
[CA2227](ca2227-collection-properties-should-be-read-only.md) | Propriedades de coleção devem ser somente leitura
[CA2229](ca2229-implement-serialization-constructors.md) | Implementar construtores de serialização
[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Sobrecarga do operador Equals no tipo de valor de substituição é igual a
[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) | Passar objetos URI do sistema em vez de cadeias de caracteres
[CA2235](ca2235-mark-all-non-serializable-fields.md) | Marcar todos os campos não serializáveis
[CA2237](ca2237-mark-iserializable-types-with-serializableattribute.md) | Marcar tipos ISerializable com serializável
[CA2241](ca2241-provide-correct-arguments-to-formatting-methods.md) | Fornecer argumentos corretos para métodos de formatação
[CA2242](ca2242-test-for-nan-correctly.md) | Testar para NaN corretamente
[CA2243](ca2243-attribute-string-literals-should-parse-correctly.md) | Literais de cadeias de caracteres de atributo devem ser analisados corretamente
CA2244 | Não duplicar inicializações de elemento indexado
[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md) | Não usar o desserializador BinaryFormatter não seguro
[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) | Não chamar BinaryFormatter.Deserialize sem antes definir BinaryFormatter.Binder
[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) | Verificar se o BinaryFormatter.Binder está definido antes de chamar BinaryFormatter.Deserialize
[CA2305](ca2305-do-not-use-insecure-deserializer-losformatter.md) | Não usar o desserializador inseguro LosFormatter
[CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md) | Não usar o desserializador inseguro NetDataContractSerializer
[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) | Não desserializar sem definir primeiro NetDataContractSerializer.Binder
[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) | Verificar se NetDataContractSerializer.Binder foi definido antes de desserializar
[CA2315](ca2315-do-not-use-insecure-deserializer-objectstateformatter.md) | Não usar o desserializador inseguro ObjectStateFormatter
[CA2321](ca2321.md) | Não desserializar com JavaScriptSerializer usando um SimpleTypeResolver
[CA2322](ca2322.md) | Garantir que o JavaScriptSerializer não seja inicializado com SimpleTypeResolver antes de desserializar
[CA3001](ca3001-review-code-for-sql-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de SQL
[CA3002](ca3002-review-code-for-xss-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de XSS
[CA3003](ca3003-review-code-for-file-path-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de caminho
[CA3004](ca3004-review-code-for-information-disclosure-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de divulgação de informações
[CA3005](ca3005-review-code-for-ldap-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de LDAP
[CA3006](ca3006-review-code-for-process-command-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de comando de processo
[CA3007](ca3007-review-code-for-open-redirect-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de redirecionamento aberto
[CA3008](ca3008-review-code-for-xpath-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de XPath
[CA3009](ca3009-review-code-for-xml-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de XML
[CA3010](ca3010-review-code-for-xaml-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de XAML
[CA3011](ca3011-review-code-for-dll-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de DLL
[CA3012](ca3012-review-code-for-regex-injection-vulnerabilities.md) | Examinar código quanto a vulnerabilidades de injeção de regex
CA3061 | Não adicionar esquema por URL
[CA3075](ca3075-insecure-dtd-processing.md) | Processamento DTD não seguro em XML
[CA3076](ca3076-insecure-xslt-script-execution.md) | Processamento de script XSLT inseguro.
[CA3077](ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader.md) | Processamento inseguro em design de API, XmlDocument e XmlTextReader
[CA3147](ca3147-mark-verb-handlers-with-validateantiforgerytoken.md) | Marcar manipuladores de verbo com o token de antifalsificação de validação
[CA5350](ca5350-do-not-use-weak-cryptographic-algorithms.md) | Não usar algoritmos de criptografia fracos
[CA5351](ca5351-do-not-use-broken-cryptographic-algorithms.md) | Não usar algoritmos de criptografia desfeitos
CA5358 | Não usar modos de codificação não seguros
CA5359 | Não desabilitar a validação de certificado
CA5360 | Não chamar métodos perigosos na desserialização
CA5361 | Não desabilitar o uso do SChannel de criptografia forte
CA5362 | Não se referir à classe serializável Self
CA5363 | Não desabilitar a validação de solicitação
CA5364 | Não usar protocolos de segurança preteridos
CA5365 | Não desabilitar a verificação de cabeçalho HTTP
CA5366 | Usar XmlReader para XML de leitura de DataSet
CA5367 | Não serializar tipos com campos de ponteiro
CA5368 | Definir ViewStateUserKey para classes derivadas da página
CA5369 | Usar XmlReader para desserializar
CA5370 | Usar XmlReader para validar o leitor
CA5371 | Usar XmlReader para leitura de esquema
CA5372 | Usar XmlReader para XPathDocument
CA5373 | Não usar função de derivação de chave obsoleta
CA5374 | Não usar XslTransform
CA5375 | Não usar assinatura de acesso compartilhado da conta
CA5376 | Usar SharedAccessProtocol HttpsOnly
CA5377 | Usar política de acesso no nível do contêiner
CA5378 | Não desabilite ServicePointManagerSecurityProtocols
CA5379 | Não usar algoritmo de função de derivação de chave fraca
CA9999 | Incompatibilidade de versão do analisador

## <a name="unported-rules"></a>Regras não portadas

O conjunto de regras que não foram modeladas para analisadores de [FxCop](install-fxcop-analyzers.md) consiste em regras que ainda não estão, mas que ainda [podem ser portadas](#rules-that-may-be-ported), e aquelas que foram preteridas e [não serão portadas](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Regras que podem ser portadas

As regras de análise de código estático do FxCop a seguir ainda não foram implementadas como analisadores, mas ainda podem ser. Isso pode ser devido a um motivo técnico de bloqueio ou simplesmente que a regra é de prioridade mais baixa. Para obter mais informações sobre o status de porta de cada regra, clique no link na coluna **problema de rastreamento** .

ID da regra | Problema de acompanhamento
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804-remove-unused-locals.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811-avoid-uncalled-private-code.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900-value-type-fields-should-be-portable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001-avoid-calling-problematic-methods.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004-remove-calls-to-gc-keepalive.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006-use-safehandle-to-encapsulate-native-resources.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109-review-visible-event-handlers.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204-literals-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205-use-managed-equivalents-of-win32-api.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212-do-not-mark-serviced-components-with-webmethod.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215-dispose-methods-should-call-base-class-dispose.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232-mark-windows-forms-entry-points-with-stathread.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236-call-base-class-methods-on-iserializable-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238-implement-serialization-methods-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239-provide-deserialization-methods-for-optional-fields.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240-implement-iserializable-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Regras preteridas

As seguintes regras de análise de código estático do FxCop foram preteridas e não serão implementadas como analisadores. Para obter mais informações, você pode pesquisar por ID de regra (por exemplo, **CA1009**) na [página de problemas do GitHub Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1702](ca1702-compound-words-should-be-cased-correctly.md)
- [CA1703](ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1800](ca1800-do-not-cast-unnecessarily.md)
- [CA1809](ca1809-avoid-excessive-locals.md)
- [CA1901](ca1901-p-invoke-declarations-should-be-portable.md)
- [CA1903](ca1903-use-only-api-from-targeted-framework.md)
- [CA2003](ca2003-do-not-treat-fibers-as-threads.md)
- [CA2102](ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)
- [CA2103](ca2103-review-imperative-security.md)
- [CA2104](ca2104-do-not-declare-read-only-mutable-reference-types.md)
- [CA2105](ca2105-array-fields-should-not-be-read-only.md)
- [CA2106](ca2106-secure-asserts.md)
- [CA2107](ca2107-review-deny-and-permit-only-usage.md)
- [CA2108](ca2108-review-declarative-security-on-value-types.md)
- [CA2111](ca2111-pointers-should-not-be-visible.md)
- [CA2112](ca2112-secured-types-should-not-expose-fields.md)
- [CA2114](ca2114-method-security-should-be-a-superset-of-type.md)
- [CA2115](ca2115-call-gc-keepalive-when-using-native-resources.md)
- [CA2116](ca2116-aptca-methods-should-only-call-aptca-methods.md)
- [CA2117](ca2117-aptca-types-should-only-extend-aptca-base-types.md)
- [CA2118](ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)
- [CA2120](ca2120-secure-serialization-constructors.md)
- [CA2121](ca2121-static-constructors-should-be-private.md)
- [CA2122](ca2122-do-not-indirectly-expose-methods-with-link-demands.md)
- [CA2123](ca2123-override-link-demands-should-be-identical-to-base.md)
- [CA2124](ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)
- [CA2126](ca2126-type-link-demands-require-inheritance-demands.md)
- [CA2130](ca2130-security-critical-constants-should-be-transparent.md)
- [CA2131](ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)
- [CA2132](ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)
- [CA2133](ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)
- [CA2134](ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)
- [CA2135](ca2135-level-2-assemblies-should-not-contain-linkdemands.md)
- [CA2136](ca2136-members-should-not-have-conflicting-transparency-annotations.md)
- [CA2137](ca2137-transparent-methods-must-contain-only-verifiable-il.md)
- [CA2138](ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)
- [CA2139](ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)
- [CA2140](ca2140-transparent-code-must-not-reference-security-critical-items.md)
- [CA2141](ca2141-transparent-methods-must-not-satisfy-linkdemands.md)
- [CA2142](ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
- [CA2143](ca2143-transparent-methods-should-not-use-security-demands.md)
- [CA2144](ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)
- [CA2145](ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)
- [CA2146](ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)
- [CA2147](ca2147-transparent-methods-may-not-use-security-asserts.md)
- [CA2149](ca2149-transparent-methods-must-not-call-into-native-code.md)
- [CA2151](ca2151-fields-with-critical-types-should-be-security-critical.md)
- [CA2202](ca2202-do-not-dispose-objects-multiple-times.md)
- [CA2210](ca2210-assemblies-should-have-valid-strong-names.md)
- [CA2220](ca2220-finalizers-should-call-base-class-finalizer.md)
- [CA2221](ca2221-finalizers-should-be-protected.md)
- [CA2222](ca2222-do-not-decrease-inherited-member-visibility.md) ([justificativa](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223-members-should-differ-by-more-than-return-type.md)
- [CA2228](ca2228-do-not-ship-unreleased-resource-formats.md)
- [CA2230](ca2230-use-params-for-variable-arguments.md)
- [CA2233](ca2233-operations-should-not-overflow.md)
- [CA5122](ca5122-p-invoke-declarations-should-not-be-safe-critical.md)

## <a name="see-also"></a>Consulte também

- [Regras Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)