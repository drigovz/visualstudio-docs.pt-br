---
title: Conjunto de regras de diretrizes do design estendido para código gerenciado
ms.date: 11/04/2016
description: Saiba mais sobre o conjunto de regras de diretrizes de design estendido no Visual Studio, que se concentra na usabilidade e na capacidade de manutenção. Consulte descrições de regra.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3555014113f84a5e21f21d1ab7d9a658e2c9aa6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860328"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Conjunto de regras de diretrizes do design estendido para código gerenciado

O conjunto de regras da regra de diretrizes de design estendido da Microsoft expande as regras básicas de diretriz de design para maximizar os problemas de usabilidade e manutenção relatados. A ênfase extra é feita nas diretrizes de nomenclatura. Você deve considerar a inclusão desse conjunto de regras se seu projeto incluir código de biblioteca ou se você quiser impor os padrões mais altos para escrever código que seja fácil de manter.

As regras de diretriz de design estendido incluem todas as regras no conjunto de regras [básicas de diretriz de diretrizes de design](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) , que inclui as regras no conjunto de regras [gerenciadas recomendadas](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

A tabela a seguir descreve todas as regras no conjunto de regras de regra de diretrizes de design estendido da Microsoft.

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
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Não declarar membros estáticos em tipos genéricos|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Não expor listas genéricas|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Usar instâncias do manipulador de eventos genérico|
|[CA1004](../code-quality/ca1004.md)|Métodos genéricos devem fornecer um parâmetro de tipo|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Evitar parâmetros excessivos em tipos genéricos|
|[CA1006](../code-quality/ca1006.md)|Não aninhar tipos genéricos em assinaturas de membro|
|[CA1007](../code-quality/ca1007.md)|Usar genéricos quando apropriado|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Enumerações devem ter valor zero|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Coleções devem implementar uma interface genérica|
|[CA1011](../code-quality/ca1011.md)|Considerar a passagem de tipos base como parâmetros|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Tipos abstratos não devem ter construtores|
|[CA1013](../code-quality/ca1013.md)|Sobrecarregar o operador equals na sobrecarga de adição e subtração|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Marcar assemblies com CLSCompliantAttribute|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Marcar assemblies com ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Marcar atributos com AttributeUsageAttribute|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Definir acessadores para argumentos de atributo|
|[CA1023](../code-quality/ca1023.md)|Indexadores não devem ser multidimensionais|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Usar propriedades quando apropriado|
|[CA1025](../code-quality/ca1025.md)|Substituir argumentos repetitivos por matriz de parâmetros|
|[CA1026](../code-quality/ca1026.md)|Parâmetros padrão não devem ser usados|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Marcar enumerações com FlagsAttribute|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|O armazenamento de enumerações deve ser Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Usar eventos quando apropriado|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Não capturar tipos de exceção geral|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementar construtores de exceção padrão|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|Tipos aninhados não devem ser visíveis|
|[CA1035](../code-quality/ca1035.md)|Implementações ICollection têm membros fortemente tipados|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Substituir métodos em tipos comparáveis|
|[CA1038](../code-quality/ca1038.md)|Enumeradores devem ser fortemente tipados|
|[CA1039](../code-quality/ca1039.md)|Listas são fortemente tipadas|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|Fornecer a mensagem ObsoleteAttribute|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Usar argumento integral ou de cadeia de caracteres para indexadores|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Propriedades não devem ser somente gravação|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Não sobrecarregar o operador equals em tipos de referência|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Não declarar membros protegidos em tipos selados|
|[CA1048](../code-quality/ca1048.md)|Não declarar membros virtuais em tipos selados|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Declarar tipos em namespaces|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Não declarar campos de instância visíveis|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Tipos de suporte estático devem ser selados|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Tipos de suporte estático não devem ter construtores|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Parâmetros de URI não devem ser cadeias de caracteres|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Valores de retorno de URI não devem ser cadeias de caracteres|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Propriedades de URI não devem ser cadeias de caracteres|
|[CA1057](../code-quality/ca1057.md)|Sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Tipos não devem estender determinados tipos base|
|[CA1059](../code-quality/ca1059.md)|Membros não devem expor determinados tipos concretos|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Exceções devem ser públicas|
|[CA1500](../code-quality/ca1500.md)|Nomes de variável não devem corresponder a nomes de campo|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Evitar complexidade excessiva|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Identificadores não devem corresponder a palavras-chave|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Examinar parâmetros não utilizados|
|[CA1804](../code-quality/ca1804.md)|Remover locais não utilizados|
|[CA1809](../code-quality/ca1809.md)|Evitar locais excessivos|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Inicializar campos estáticos de tipo de referência em linha|
|[CA1811](../code-quality/ca1811.md)|Evitar código particular não chamado|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Evitar classes internas sem instâncias|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Evitar atributos não selados|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Preferir matrizes denteadas a matrizes multidimensionais|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Substituir equals e o operador equals em tipos de valor|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Propriedades não devem retornar matrizes|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Marcar membros como estáticos|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Evitar campos particulares não utilizados|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Não acionar tipos de exceção reservados|
|[CA2205](../code-quality/ca2205.md)|Usar equivalentes gerenciados da API do Win32|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Criar instância de exceções de argumento corretamente|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Campos não constantes não devem ser visíveis|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Não marcar enumerações com FlagsAttribute|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Não acionar exceções em cláusulas de exceção|
|[CA2221](../code-quality/ca2221.md)|Os finalizadores devem ser protegidos|
|[CA2222](../code-quality/ca2222.md)|Não diminuir a visibilidade dos membros herdados|
|[CA2223](../code-quality/ca2223.md)|Os membros devem ser diferentes em algo além de um tipo de retorno|
|[CA2224](../code-quality/ca2224.md)|Substituir equals ao sobrecarregar operador equals|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Sobrecargas de operador têm alternativas nomeadas|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operadores devem ter sobrecargas simétricas|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Propriedades de coleção devem ser somente leitura|
|[CA2230](../code-quality/ca2230.md)|Usar parâmetros para argumentos variáveis|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Passar objetos System.Uri em vez de cadeias de caracteres|
|[CA2239](../code-quality/ca2239.md)|Fornecer métodos de desserialização para campos opcionais|
|[CA1020](../code-quality/ca1020.md)|Evitar namespaces com poucos tipos|
|[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021)|Evitar parâmetros out|
|[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040)|Evitar interfaces vazias|
|[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045)|Não passar tipos por referência|
|[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062)|Validar argumentos de métodos públicos|
|[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)|Evitar herança excessiva|
|[CA1504](../code-quality/ca1504.md)|Examinar nomes de campo confusos|
|[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)|Evitar código de difícil manutenção|
|[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)|Evitar acoplamento de classes excessivo|
|[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700)|Não nomear valores de enumeração 'Reserved'|
|[CA1701](../code-quality/ca1701.md)|Palavras compostas de cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas|
|[CA1702](../code-quality/ca1702.md)|Palavras compostas devem ter maiúsculas e minúsculas corretas|
|[CA1703](../code-quality/ca1703.md)|Cadeias de caracteres de recurso devem ser escritas corretamente|
|[CA1704](../code-quality/ca1704.md)|Identificadores devem ser escritos corretamente|
|[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707)|Identificadores não devem conter sublinhados|
|[CA1709](../code-quality/ca1709.md)|Identificadores devem ter maiúsculas e minúsculas corretas|
|[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)|Identificadores devem ter um sufixo correto|
|[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711)|Identificadores não devem ter um sufixo incorreto|
|[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712)|Não prefixar valores de enumeração com um nome de tipo|
|[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713)|Eventos não devem ter o prefixo anterior ou posterior|
|[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714)|Enumerações de sinalizador devem ter nomes no plural|
|[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715)|Identificadores devem ter um prefixo correto|
|[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717)|Apenas enumerações FlagsAttribute devem ter nomes no plural|
|[CA1719](../code-quality/ca1719.md)|Nomes de parâmetros não devem corresponder a nomes de membros|
|[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720)|Identificadores não devem conter nomes de tipos|
|[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721)|Nomes de propriedades não devem corresponder a métodos get|
|[CA1722](../code-quality/ca1722.md)|Identificadores não devem ter um prefixo incorreto|
|[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724)|Nomes de tipos não devem corresponder a namespaces|
|[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725)|Nomes de parâmetros devem corresponder à declaração base|
|[CA1726](../code-quality/ca1726.md)|Usar termos preferenciais|
|[CA2204](../code-quality/ca2204.md)|Literais devem ser escritos corretamente|
