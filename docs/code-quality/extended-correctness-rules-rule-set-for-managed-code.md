---
title: Conjunto de regras de correção estendido para código gerenciado
ms.date: 11/04/2016
description: Saiba mais sobre o conjunto de regras de correções estendidas no Visual Studio, que é útil para interoperabilidade COM e aplicativos móveis. Consulte descrições de regra.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: a70a0315d596e4490d40db1846d7be0b6f3bf448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860367"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Conjunto de regras de correção estendido para código gerenciado

O conjunto de regras de regras de correção estendida da Microsoft maximiza os erros de uso de lógica e de estrutura que são relatados pela análise de código. A ênfase extra é feita em cenários específicos, como interoperabilidade COM e aplicativos móveis. Você deve considerar a inclusão desse conjunto de regras se um desses cenários se aplicar ao seu projeto ou para encontrar problemas adicionais em seu projeto.

O conjunto de regras de regras de correção estendida da Microsoft inclui as regras que estão no conjunto de regras [regras de exatidão básicas](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) , que contém as regras que estão no conjunto de regras [gerenciadas recomendadas](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

A tabela a seguir descreve todas as regras no conjunto de regras de regras de correção estendida da Microsoft.

|Regra|Descrição|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Tipos com campos descartáveis devem ser descartáveis|
|[CA1009](../code-quality/ca1009.md)|Declarar manipuladores de eventos corretamente|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Marcar assemblies com AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Métodos de interface devem ser chamados por tipos filho|
|[CA1049](../code-quality/ca1049.md)|Tipos com recursos nativos devem ser descartáveis|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Mova P/Invokes para a classe NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Não ocultar métodos de classe base|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implementar IDisposable corretamente|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Não acionar exceções em locais inesperados|
|[CA1301](../code-quality/ca1301.md)|Evitar aceleradores duplicados|
|[CA1400](../code-quality/ca1400.md)|Deve haver pontos de entrada P/Invoke|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|P/Invokes não devem ser visíveis|
|[CA1403](../code-quality/ca1403.md)|Tipos de layout automático não devem ser visíveis no COM|
|[CA1404](../code-quality/ca1404.md)|Chamar GetLastError imediatamente após P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Tipos base de tipo visível no COM devem ser visíveis no COM|
|[CA1410](../code-quality/ca1410.md)|Métodos de registro COM devem ser correspondidos|
|[CA1415](../code-quality/ca1415.md)|Declarar P/Invokes corretamente|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Remover finalizadores vazios|
|[CA1900](../code-quality/ca1900.md)|Campos de tipo de valor devem ser portáteis|
|[CA1901](../code-quality/ca1901.md)|Declarações P/Invoke devem ser portáteis|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Não bloquear objetos com identidade fraca|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Examinar consultas SQL em busca de vulnerabilidades de segurança|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|
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
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Relançar para preservar detalhes da pilha|
|[CA2202](../code-quality/ca2202.md)|Não descartar objetos várias vezes|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Inicializar campos estáticos de tipo de valor em linha|
|[CA2212](../code-quality/ca2212.md)|Não marcar componentes atendidos com WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Campos descartáveis devem ser descartados|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Não chamar métodos substituíveis em construtores|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Tipos descartáveis devem declarar o finalizador|
|[CA2220](../code-quality/ca2220.md)|Os finalizadores devem chamar o finalizador de classe base|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implementar construtores de serialização|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Sobrecarregar operador equals ao substituir ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar pontos de entrada do Windows Forms com STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Marcar todos os campos não serializáveis|
|[CA2236](../code-quality/ca2236.md)|Chamar métodos da classe base em tipos ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Marcar tipos ISerializable com SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialização corretamente|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable corretamente|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Fornecer argumentos corretos para métodos de formatação|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Testar para NaN corretamente|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Enumerações devem ter valor zero|
|[CA1013](../code-quality/ca1013.md)|Sobrecarregar o operador equals na sobrecarga de adição e subtração|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Não passar literais como parâmetros localizados|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizar cadeias de caracteres em maiúsculas|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|Não ignorar resultados do método|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|Chamar GC.SuppressFinalize corretamente|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Propriedades não devem retornar matrizes|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres|
|[CA1903](../code-quality/ca1903.md)|Usar apenas a API da estrutura de destino|
|[CA2004](../code-quality/ca2004.md)|Remover as chamadas a GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Usar SafeHandle para encapsular recursos nativos|
|[CA2102](../code-quality/ca2102.md)|Capturar exceções não CLSCompliant em manipuladores gerais|
|[CA2104](../code-quality/ca2104.md)|Não declarar tipos de referência mutáveis somente leitura|
|[CA2105](../code-quality/ca2105.md)|Campos de matrizes não devem ser somente leitura|
|[CA2106](../code-quality/ca2106.md)|Declarações seguras|
|[CA2115](../code-quality/ca2115.md)|Chamar GC.KeepAlive ao usar recursos nativos|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Selar métodos que atendem a interfaces particulares|
|[CA2120](../code-quality/ca2120.md)|Construtores de serialização seguros|
|[CA2121](../code-quality/ca2121.md)|Construtores estáticos devem ser particulares|
|[CA2130](../code-quality/ca2130.md)|Constantes críticas de segurança devem ser transparentes|
|[CA2205](../code-quality/ca2205.md)|Usar equivalentes gerenciados da API do Win32|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Métodos Dispose devem chamar o descarte da classe base|
|[CA2221](../code-quality/ca2221.md)|Os finalizadores devem ser protegidos|
|[CA2222](../code-quality/ca2222.md)|Não diminuir a visibilidade dos membros herdados|
|[CA2223](../code-quality/ca2223.md)|Os membros devem ser diferentes em algo além de um tipo de retorno|
|[CA2224](../code-quality/ca2224.md)|Substituir equals ao sobrecarregar operador equals|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operadores devem ter sobrecargas simétricas|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Propriedades de coleção devem ser somente leitura|
|[CA2239](../code-quality/ca2239.md)|Fornecer métodos de desserialização para campos opcionais|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementar construtores de exceção padrão|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Parâmetros de URI não devem ser cadeias de caracteres|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Valores de retorno de URI não devem ser cadeias de caracteres|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Propriedades de URI não devem ser cadeias de caracteres|
|[CA1057](../code-quality/ca1057.md)|Sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri|
|[CA1402](../code-quality/ca1402.md)|Evitar sobrecargas em interfaces visíveis no COM|
|[CA1406](../code-quality/ca1406.md)|Evitar argumentos Int64 para clientes do Visual Basic 6|
|[CA1407](../code-quality/ca1407.md)|Evitar membros estáticos em tipos visíveis no COM|
|[CA1408](../code-quality/ca1408.md)|Não usar AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409.md)|Tipos visíveis no COM devem poder ser criados|
|[CA1411](../code-quality/ca1411.md)|Métodos de registro COM não devem ser visíveis|
|[CA1412](../code-quality/ca1412.md)|Marcar interfaces ComSource como IDispatch|
|[CA1413](../code-quality/ca1413.md)|Evitar campos não públicos em tipos de valor visíveis no COM|
|[CA1414](../code-quality/ca1414.md)|Marcar argumentos P/Invoke boolianos com MarshalAs|
|[CA1600](../code-quality/ca1600.md)|Não usar prioridade de processo ociosa|
|[CA1601](../code-quality/ca1601.md)|Não usar temporizadores que impedem alterações no estado de energia|
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|Marque assemblies com NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001.md)|Evitar chamar métodos problemáticos|
|[CA2003](../code-quality/ca2003.md)|Não tratar fibras como threads|
|[CA2135](../code-quality/ca2135.md)|Os assemblies de nível 2 não devem conter LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Membros não devem ter anotações de transparência conflitantes|
|[CA2139](../code-quality/ca2139.md)|Métodos transparentes podem não usar o atributo HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142.md)|O código transparente não deve ser protegido com LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Métodos transparentes não devem usar demandas de segurança|
|[CA2144](../code-quality/ca2144.md)|O código transparente não deve carregar assemblies de matrizes de bytes|
|[CA2145](../code-quality/ca2145.md)|Métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|Literais devem ser escritos corretamente|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Campos não constantes não devem ser visíveis|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Não marcar enumerações com FlagsAttribute|
|[CA2218](../code-quality/ca2218.md)|Substituir GetHashCode ao substituir Equals|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Não acionar exceções em cláusulas de exceção|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Sobrecargas de operador têm alternativas nomeadas|
|[CA2228](../code-quality/ca2228.md)|Não fornecer formatos de recurso não lançados|
|[CA2230](../code-quality/ca2230.md)|Usar parâmetros para argumentos variáveis|
|[CA2233](../code-quality/ca2233.md)|As operações não devem estourar|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Passar objetos System.Uri em vez de cadeias de caracteres|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|Literais de cadeias de caracteres de atributo devem ser analisados corretamente|
