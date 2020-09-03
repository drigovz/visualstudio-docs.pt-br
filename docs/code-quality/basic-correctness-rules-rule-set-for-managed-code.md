---
title: Conjunto de regras de correção básico para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c38d8bc2eefe9c6116f9bde93e475cf332591471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75573229"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Conjunto de regras de correção básico para código gerenciado

O conjunto de regras básicas de regras de correção se concentra em erros lógicos e erros comuns no uso de APIs de estrutura. As regras básicas de correção incluem as regras no conjunto de regras de regra [recomendadas gerenciadas](managed-recommended-rules-rule-set-for-managed-code.md) .

A tabela a seguir descreve todas as regras do conjunto de regras de regras de correção básica da Microsoft.

|Regra|Descrição|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Tipos com campos descartáveis devem ser descartáveis|
|[CA1009](../code-quality/ca1009.md)|Declarar manipuladores de eventos corretamente|
|[CA1016](../code-quality/ca1016.md)|Marcar assemblies com AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|Métodos de interface devem ser chamados por tipos filho|
|[CA1049](../code-quality/ca1049.md)|Tipos com recursos nativos devem ser descartáveis|
|[CA1060](../code-quality/ca1060.md)|Mova P/Invokes para a classe NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Não ocultar métodos de classe base|
|[CA1063](../code-quality/ca1063.md)|Implementar IDisposable corretamente|
|[CA1065](../code-quality/ca1065.md)|Não acionar exceções em locais inesperados|
|[CA1301](../code-quality/ca1301.md)|Evitar aceleradores duplicados|
|[CA1400](../code-quality/ca1400.md)|Deve haver pontos de entrada P/Invoke|
|[CA1401](../code-quality/ca1401.md)|P/Invokes não devem ser visíveis|
|[CA1403](../code-quality/ca1403.md)|Tipos de layout automático não devem ser visíveis no COM|
|[CA1404](../code-quality/ca1404.md)|Chamar GetLastError imediatamente após P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Tipos base de tipo visível no COM devem ser visíveis no COM|
|[CA1410](../code-quality/ca1410.md)|Métodos de registro COM devem ser correspondidos|
|[CA1415](../code-quality/ca1415.md)|Declarar P/Invokes corretamente|
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
|[CA1008](../code-quality/ca1008.md)|Enumerações devem ter valor zero|
|[CA1013](../code-quality/ca1013.md)|Sobrecarregar o operador equals na sobrecarga de adição e subtração|
|[CA1303](../code-quality/ca1303.md)|Não passar literais como parâmetros localizados|
|[CA1308](../code-quality/ca1308.md)|Normalizar cadeias de caracteres em maiúsculas|
|[CA1806](../code-quality/ca1806.md)|Não ignorar resultados do método|
|[CA1816](../code-quality/ca1816.md)|Chamar GC.SuppressFinalize corretamente|
|[CA1819](../code-quality/ca1819.md)|Propriedades não devem retornar matrizes|
|[CA1820](../code-quality/ca1820.md)|Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres|
|[CA1903](../code-quality/ca1903.md)|Usar apenas a API da estrutura de destino|
|[CA2004](../code-quality/ca2004.md)|Remover as chamadas a GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Usar SafeHandle para encapsular recursos nativos|
|[CA2102](../code-quality/ca2102.md)|Capturar exceções não CLSCompliant em manipuladores gerais|
|[CA2104](../code-quality/ca2104.md)|Não declarar tipos de referência mutáveis somente leitura|
|[CA2105](../code-quality/ca2105.md)|Campos de matrizes não devem ser somente leitura|
|[CA2106](../code-quality/ca2106.md)|Declarações seguras|
|[CA2115](../code-quality/ca2115.md)|Chamar GC.KeepAlive ao usar recursos nativos|
|[CA2119](../code-quality/ca2119.md)|Selar métodos que atendem a interfaces particulares|
|[CA2120](../code-quality/ca2120.md)|Construtores de serialização seguros|
|[CA2121](../code-quality/ca2121.md)|Construtores estáticos devem ser particulares|
|[CA2130](../code-quality/ca2130.md)|Constantes críticas de segurança devem ser transparentes|
|[CA2205](../code-quality/ca2205.md)|Usar equivalentes gerenciados da API do Win32|
|[CA2215](../code-quality/ca2215.md)|Métodos Dispose devem chamar o descarte da classe base|
|[CA2221](../code-quality/ca2221.md)|Os finalizadores devem ser protegidos|
|[CA2222](../code-quality/ca2222.md)|Não diminuir a visibilidade dos membros herdados|
|[CA2223](../code-quality/ca2223.md)|Os membros devem ser diferentes em algo além de um tipo de retorno|
|[CA2224](../code-quality/ca2224.md)|Substituir equals ao sobrecarregar operador equals|
|[CA2226](../code-quality/ca2226.md)|Operadores devem ter sobrecargas simétricas|
|[CA2227](../code-quality/ca2227.md)|Propriedades de coleção devem ser somente leitura|
|[CA2239](../code-quality/ca2239.md)|Fornecer métodos de desserialização para campos opcionais|
