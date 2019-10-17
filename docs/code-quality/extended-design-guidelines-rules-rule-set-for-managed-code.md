---
title: Conjunto de regras de diretrizes do design estendido para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a2e3d6b626e12df626903f2c26f93d779288a921
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449079"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Conjunto de regras de diretrizes do design estendido para código gerenciado

O conjunto de regras da regra de diretrizes de design estendido da Microsoft expande as regras básicas de diretriz de design para maximizar os problemas de usabilidade e manutenção relatados. A ênfase extra é feita nas diretrizes de nomenclatura. Você deve considerar a inclusão desse conjunto de regras se seu projeto incluir código de biblioteca ou se você quiser impor os padrões mais altos para escrever código que seja fácil de manter.

As regras de diretriz de design estendido incluem todas as regras no conjunto de regras [básicas de diretriz de diretrizes de design](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) , que inclui as regras no conjunto de regras [gerenciadas recomendadas](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

A tabela a seguir descreve todas as regras no conjunto de regras de regra de diretrizes de design estendido da Microsoft.

|Regra|Descrição|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Tipos com campos descartáveis devem ser descartáveis|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Declarar manipuladores de eventos corretamente|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marcar assemblies com AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Métodos de interface devem ser chamados por tipos filho|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Tipos com recursos nativos devem ser descartáveis|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Mova P/Invokes para a classe NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Não ocultar métodos de classe base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementar IDisposable corretamente|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Não acionar exceções em locais inesperados|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar aceleradores duplicados|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Deve haver pontos de entrada P/Invoke|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes não devem ser visíveis|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Tipos de layout automático não devem ser visíveis no COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Chamar GetLastError imediatamente após P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Tipos base de tipo visível no COM devem ser visíveis no COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Métodos de registro COM devem ser correspondidos|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Declarar P/Invokes corretamente|
|[CA1821](../code-quality/ca1821.md)|Remover finalizadores vazios|
|[CA1900](../code-quality/ca1900.md)|Campos de tipo de valor devem ser portáteis|
|[CA1901](../code-quality/ca1901.md)|Declarações P/Invoke devem ser portáteis|
|[CA2002](../code-quality/ca2002.md)|Não bloquear objetos com identidade fraca|
|[CA2100](../code-quality/ca2100.md)|Examinar consultas SQL em busca de vulnerabilidades de segurança|
|[CA2101](../code-quality/ca2101.md)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Examinar a segurança declarativa em tipos de valor|
|[CA2111](../code-quality/ca2111.md)|Ponteiros não devem ser visíveis|
|[CA2112](../code-quality/ca2112.md)|Tipos protegidos não devem expor campos|
|[CA2114](../code-quality/ca2114.md)|A segurança do método deve ser um superconjunto do tipo|
|[CA2116](../code-quality/ca2116.md)|Métodos APTCA devem chamar somente métodos APTCA|
|[CA2117](../code-quality/ca2117.md)|Tipos APTCA devem estender somente tipos base APTCA|
|[CA2122](../code-quality/ca2122.md)|Não expor indiretamente métodos com demandas de link|
|[CA2123](../code-quality/ca2123.md)|As demandas de link de substituição devem ser idênticas à base|
|[CA2124](../code-quality/ca2124.md)|Encapsular cláusulas finally vulneráveis em try externo|
|[CA2126](../code-quality/ca2126.md)|As demandas de link de tipo exigem demandas de herança|
|[CA2131](../code-quality/ca2131.md)|Tipos críticos de segurança podem não participar da equivalência de tipo|
|[CA2132](../code-quality/ca2132.md)|Construtores padrão devem ser pelo menos tão críticos quanto construtores padrão do tipo base|
|[CA2133](../code-quality/ca2133.md)|Representantes devem ser associados a métodos com transparência consistente|
|[CA2134](../code-quality/ca2134.md)|Os métodos devem manter uma transparência consistente durante a substituição dos métodos base|
|[CA2137](../code-quality/ca2137.md)|Métodos transparentes devem conter apenas a IL verificável|
|[CA2138](../code-quality/ca2138.md)|Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|O código transparente não deve referenciar itens críticos de segurança|
|[CA2141](../code-quality/ca2141.md)|Métodos transparentes não devem satisfazer LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Os tipos devem ser pelo menos tão críticos quanto seus tipos base e interfaces|
|[CA2147](../code-quality/ca2147.md)|Métodos transparentes podem não usar declarações de segurança|
|[CA2149](../code-quality/ca2149.md)|Métodos transparentes não devem chamar código nativo|
|[CA2200](../code-quality/ca2200.md)|Relançar para preservar detalhes da pilha|
|[CA2202](../code-quality/ca2202.md)|Não descartar objetos várias vezes|
|[CA2207](../code-quality/ca2207.md)|Inicializar campos estáticos de tipo de valor em linha|
|[CA2212](../code-quality/ca2212.md)|Não marcar componentes atendidos com WebMethod|
|[CA2213](../code-quality/ca2213.md)|Campos descartáveis devem ser descartados|
|[CA2214](../code-quality/ca2214.md)|Não chamar métodos substituíveis em construtores|
|[CA2216](../code-quality/ca2216.md)|Tipos descartáveis devem declarar o finalizador|
|[CA2220](../code-quality/ca2220.md)|Os finalizadores devem chamar o finalizador de classe base|
|[CA2229](../code-quality/ca2229.md)|Implementar construtores de serialização|
|[CA2231](../code-quality/ca2231.md)|Sobrecarregar operador equals ao substituir ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar pontos de entrada do Windows Forms com STAThread|
|[CA2235](../code-quality/ca2235.md)|Marcar todos os campos não serializáveis|
|[CA2236](../code-quality/ca2236.md)|Chamar métodos da classe base em tipos ISerializable|
|[CA2237](../code-quality/ca2237.md)|Marcar tipos ISerializable com SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialização corretamente|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable corretamente|
|[CA2241](../code-quality/ca2241.md)|Fornecer argumentos corretos para métodos de formatação|
|[CA2242](../code-quality/ca2242.md)|Testar para NaN corretamente|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Não declarar membros estáticos em tipos genéricos|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Não expor listas genéricas|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Usar instâncias do manipulador de eventos genérico|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Métodos genéricos devem fornecer um parâmetro de tipo|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Evitar parâmetros excessivos em tipos genéricos|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Não aninhar tipos genéricos em assinaturas de membro|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Usar genéricos quando apropriado|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Enumerações devem ter valor zero|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Coleções devem implementar uma interface genérica|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Considerar a passagem de tipos base como parâmetros|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Tipos abstratos não devem ter construtores|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Sobrecarregar o operador equals na sobrecarga de adição e subtração|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Marcar assemblies com CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Marcar assemblies com ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Marcar atributos com AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Definir acessadores para argumentos de atributo|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Indexadores não devem ser multidimensionais|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Usar propriedades quando apropriado|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Substituir argumentos repetitivos por matriz de parâmetros|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Parâmetros padrão não devem ser usados|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Marcar enumerações com FlagsAttribute|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|O armazenamento de enumerações deve ser Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Usar eventos quando apropriado|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Não capturar tipos de exceção geral|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementar construtores de exceção padrão|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Tipos aninhados não devem ser visíveis|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Implementações ICollection têm membros fortemente tipados|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Substituir métodos em tipos comparáveis|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Enumeradores devem ser fortemente tipados|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listas são fortemente tipadas|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Fornecer a mensagem ObsoleteAttribute|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Usar argumento integral ou de cadeia de caracteres para indexadores|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Propriedades não devem ser somente gravação|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Não sobrecarregar o operador equals em tipos de referência|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Não declarar membros protegidos em tipos selados|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Não declarar membros virtuais em tipos selados|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Declarar tipos em namespaces|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Não declarar campos de instância visíveis|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Tipos de suporte estático devem ser selados|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Tipos de suporte estático não devem ter construtores|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parâmetros de URI não devem ser cadeias de caracteres|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Valores de retorno de URI não devem ser cadeias de caracteres|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Propriedades de URI não devem ser cadeias de caracteres|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Tipos não devem estender determinados tipos base|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Membros não devem expor determinados tipos concretos|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Exceções devem ser públicas|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Nomes de variável não devem corresponder a nomes de campo|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Evitar complexidade excessiva|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Identificadores não devem corresponder a palavras-chave|
|[CA1801](../code-quality/ca1801.md)|Examinar parâmetros não utilizados|
|[CA1804](../code-quality/ca1804.md)|Remover locais não utilizados|
|[CA1809](../code-quality/ca1809.md)|Evitar locais excessivos|
|[CA1810](../code-quality/ca1810.md)|Inicializar campos estáticos de tipo de referência em linha|
|[CA1811](../code-quality/ca1811.md)|Evitar código particular não chamado|
|[CA1812](../code-quality/ca1812.md)|Evitar classes internas sem instâncias|
|[CA1813](../code-quality/ca1813.md)|Evitar atributos não selados|
|[CA1814](../code-quality/ca1814.md)|Preferir matrizes denteadas a matrizes multidimensionais|
|[CA1815](../code-quality/ca1815.md)|Substituir equals e o operador equals em tipos de valor|
|[CA1819](../code-quality/ca1819.md)|Propriedades não devem retornar matrizes|
|[CA1820](../code-quality/ca1820.md)|Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres|
|[CA1822](../code-quality/ca1822.md)|Marcar membros como estáticos|
|[CA1823](../code-quality/ca1823.md)|Evitar campos particulares não utilizados|
|[CA2201](../code-quality/ca2201.md)|Não acionar tipos de exceção reservados|
|[CA2205](../code-quality/ca2205.md)|Usar equivalentes gerenciados da API do Win32|
|[CA2208](../code-quality/ca2208.md)|Criar instância de exceções de argumento corretamente|
|[CA2211](../code-quality/ca2211.md)|Campos não constantes não devem ser visíveis|
|[CA2217](../code-quality/ca2217.md)|Não marcar enumerações com FlagsAttribute|
|[CA2219](../code-quality/ca2219.md)|Não acionar exceções em cláusulas de exceção|
|[CA2221](../code-quality/ca2221.md)|Os finalizadores devem ser protegidos|
|[CA2222](../code-quality/ca2222.md)|Não diminuir a visibilidade dos membros herdados|
|[CA2223](../code-quality/ca2223.md)|Os membros devem ser diferentes em algo além de um tipo de retorno|
|[CA2224](../code-quality/ca2224.md)|Substituir equals ao sobrecarregar operador equals|
|[CA2225](../code-quality/ca2225.md)|Sobrecargas de operador têm alternativas nomeadas|
|[CA2226](../code-quality/ca2226.md)|Operadores devem ter sobrecargas simétricas|
|[CA2227](../code-quality/ca2227.md)|Propriedades de coleção devem ser somente leitura|
|[CA2230](../code-quality/ca2230.md)|Usar parâmetros para argumentos variáveis|
|[CA2234](../code-quality/ca2234.md)|Passar objetos System.Uri em vez de cadeias de caracteres|
|[CA2239](../code-quality/ca2239.md)|Fornecer métodos de desserialização para campos opcionais|
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Evitar namespaces com poucos tipos|
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Evitar parâmetros out|
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|Evitar interfaces vazias|
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Não passar tipos por referência|
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Validar argumentos de métodos públicos|
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Evitar herança excessiva|
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Examinar nomes de campo confusos|
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|Evitar código de difícil manutenção|
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Evitar acoplamento de classes excessivo|
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Não nomear valores de enumeração 'Reserved'|
|[CA1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Palavras compostas de cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas|
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Palavras compostas devem ter maiúsculas e minúsculas corretas|
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Cadeias de caracteres de recurso devem ser escritas corretamente|
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Identificadores devem ser escritos corretamente|
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Identificadores não devem conter sublinhados|
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Identificadores devem ter maiúsculas e minúsculas corretas|
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Identificadores devem ter um sufixo correto|
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Identificadores não devem ter um sufixo incorreto|
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Não prefixar valores de enumeração com um nome de tipo|
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Eventos não devem ter o prefixo anterior ou posterior|
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Enumerações de sinalizador devem ter nomes no plural|
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Identificadores devem ter um prefixo correto|
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Apenas enumerações FlagsAttribute devem ter nomes no plural|
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Nomes de parâmetros não devem corresponder a nomes de membros|
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Identificadores não devem conter nomes de tipos|
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Nomes de propriedades não devem corresponder a métodos get|
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Identificadores não devem ter um prefixo incorreto|
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Nomes de tipos não devem corresponder a namespaces|
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Nomes de parâmetros devem corresponder à declaração base|
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Usar termos preferenciais|
|[CA2204](../code-quality/ca2204.md)|Literais devem ser escritos corretamente|
