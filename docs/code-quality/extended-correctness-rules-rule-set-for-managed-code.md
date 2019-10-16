---
title: Conjunto de regras de correção estendido para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 96a0b43e6d300d3db425cb7a926d0196566d178b
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349634"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Conjunto de regras de correção estendido para código gerenciado

O conjunto de regras de regras de correção estendida da Microsoft maximiza os erros de uso de lógica e de estrutura que são relatados pela análise de código. A ênfase extra é feita em cenários específicos, como interoperabilidade COM e aplicativos móveis. Você deve considerar a inclusão desse conjunto de regras se um desses cenários se aplicar ao seu projeto ou para encontrar problemas adicionais em seu projeto.

O conjunto de regras de regras de correção estendida da Microsoft inclui as regras que estão no conjunto de regras [regras de exatidão básicas](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) , que contém as regras que estão no conjunto de regras [gerenciadas recomendadas](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

A tabela a seguir descreve todas as regras no conjunto de regras de regras de correção estendida da Microsoft.

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
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Campos de tipo de valor devem ser portáteis|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Declarações P/Invoke devem ser portáteis|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Não bloquear objetos com identidade fraca|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Examinar consultas SQL em busca de vulnerabilidades de segurança|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Examinar a segurança declarativa em tipos de valor|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Ponteiros não devem ser visíveis|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Tipos protegidos não devem expor campos|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|A segurança do método deve ser um superconjunto do tipo|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Métodos APTCA devem chamar somente métodos APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Tipos APTCA devem estender somente tipos base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Não expor indiretamente métodos com demandas de link|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|As demandas de link de substituição devem ser idênticas à base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Encapsular cláusulas finally vulneráveis em try externo|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|As demandas de link de tipo exigem demandas de herança|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Tipos críticos de segurança podem não participar da equivalência de tipo|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Construtores padrão devem ser pelo menos tão críticos quanto construtores padrão do tipo base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Representantes devem ser associados a métodos com transparência consistente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Os métodos devem manter uma transparência consistente durante a substituição dos métodos base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Métodos transparentes devem conter apenas a IL verificável|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|O código transparente não deve referenciar itens críticos de segurança|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Métodos transparentes não devem satisfazer LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Os tipos devem ser pelo menos tão críticos quanto seus tipos base e interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Métodos transparentes podem não usar declarações de segurança|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Métodos transparentes não devem chamar código nativo|
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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Enumerações devem ter valor zero|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Sobrecarregar o operador equals na sobrecarga de adição e subtração|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Não passar literais como parâmetros localizados|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizar cadeias de caracteres em maiúsculas|
|[CA1806](../code-quality/ca1806.md)|Não ignorar resultados do método|
|[CA1816](../code-quality/ca1816.md)|Chamar GC.SuppressFinalize corretamente|
|[CA1819](../code-quality/ca1819.md)|Propriedades não devem retornar matrizes|
|[CA1820](../code-quality/ca1820.md)|Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Usar apenas a API da estrutura de destino|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Remover as chamadas a GC.KeepAlive|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Usar SafeHandle para encapsular recursos nativos|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Capturar exceções não CLSCompliant em manipuladores gerais|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Não declarar tipos de referência mutáveis somente leitura|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Campos de matrizes não devem ser somente leitura|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Declarações seguras|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Chamar GC.KeepAlive ao usar recursos nativos|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Selar métodos que atendem a interfaces particulares|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Construtores de serialização seguros|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Construtores estáticos devem ser particulares|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Constantes críticas de segurança devem ser transparentes|
|[CA2205](../code-quality/ca2205.md)|Usar equivalentes gerenciados da API do Win32|
|[CA2215](../code-quality/ca2215.md)|Métodos Dispose devem chamar o descarte da classe base|
|[CA2221](../code-quality/ca2221.md)|Os finalizadores devem ser protegidos|
|[CA2222](../code-quality/ca2222.md)|Não diminuir a visibilidade dos membros herdados|
|[CA2223](../code-quality/ca2223.md)|Os membros devem ser diferentes em algo além de um tipo de retorno|
|[CA2224](../code-quality/ca2224.md)|Substituir equals ao sobrecarregar operador equals|
|[CA2226](../code-quality/ca2226.md)|Operadores devem ter sobrecargas simétricas|
|[CA2227](../code-quality/ca2227.md)|Propriedades de coleção devem ser somente leitura|
|[CA2239](../code-quality/ca2239.md)|Fornecer métodos de desserialização para campos opcionais|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementar construtores de exceção padrão|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parâmetros de URI não devem ser cadeias de caracteres|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Valores de retorno de URI não devem ser cadeias de caracteres|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Propriedades de URI não devem ser cadeias de caracteres|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Evitar sobrecargas em interfaces visíveis no COM|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Evitar argumentos Int64 para clientes do Visual Basic 6|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Evitar membros estáticos em tipos visíveis no COM|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Não usar AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Tipos visíveis no COM devem poder ser criados|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Métodos de registro COM não devem ser visíveis|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Marcar interfaces ComSource como IDispatch|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Evitar campos não públicos em tipos de valor visíveis no COM|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Marcar argumentos P/Invoke boolianos com MarshalAs|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Não usar prioridade de processo ociosa|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Não usar temporizadores que impedem alterações no estado de energia|
|[CA1824](../code-quality/ca1824.md)|Marque assemblies com NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Evitar chamar métodos problemáticos|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Não tratar fibras como threads|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Os assemblies de nível 2 não devem conter LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Membros não devem ter anotações de transparência conflitantes|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Métodos transparentes podem não usar o atributo HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|O código transparente não deve ser protegido com LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Métodos transparentes não devem usar demandas de segurança|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|O código transparente não deve carregar assemblies de matrizes de bytes|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|Literais devem ser escritos corretamente|
|[CA2211](../code-quality/ca2211.md)|Campos não constantes não devem ser visíveis|
|[CA2217](../code-quality/ca2217.md)|Não marcar enumerações com FlagsAttribute|
|[CA2218](../code-quality/ca2218.md)|Substituir GetHashCode ao substituir Equals|
|[CA2219](../code-quality/ca2219.md)|Não acionar exceções em cláusulas de exceção|
|[CA2225](../code-quality/ca2225.md)|Sobrecargas de operador têm alternativas nomeadas|
|[CA2228](../code-quality/ca2228.md)|Não fornecer formatos de recurso não lançados|
|[CA2230](../code-quality/ca2230.md)|Usar parâmetros para argumentos variáveis|
|[CA2233](../code-quality/ca2233.md)|As operações não devem estourar|
|[CA2234](../code-quality/ca2234.md)|Passar objetos System.Uri em vez de cadeias de caracteres|
|[CA2243](../code-quality/ca2243.md)|Literais de cadeias de caracteres de atributo devem ser analisados corretamente|