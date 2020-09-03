---
title: Conjunto de regras de segurança para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 49fe666884c3a96a5c8eb632308e7f732150805e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75929219"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Conjunto de regras de segurança para código gerenciado

Use o conjunto de regras do Microsoft Security Rules para análise de código herdado para maximizar o número de possíveis problemas de segurança que são relatados.

|Regra|Descrição|
|----------|-----------------|
|[CA2100](../code-quality/ca2100.md)|Examinar consultas SQL em busca de vulnerabilidades de segurança|
|[CA2102](../code-quality/ca2102.md)|Capturar exceções não CLSCompliant em manipuladores gerais|
|[CA2103](../code-quality/ca2103.md)|Examinar a segurança imperativa|
|[CA2104](../code-quality/ca2104.md)|Não declarar tipos de referência mutáveis somente leitura|
|[CA2105](../code-quality/ca2105.md)|Campos de matrizes não devem ser somente leitura|
|[CA2106](../code-quality/ca2106.md)|Declarações seguras|
|[CA2107](../code-quality/ca2107.md)|Examinar uso de deny e permit only|
|[CA2108](../code-quality/ca2108.md)|Examinar a segurança declarativa em tipos de valor|
|[CA2109](../code-quality/ca2109.md)|Examinar manipuladores de eventos visíveis|
|[CA2111](../code-quality/ca2111.md)|Ponteiros não devem ser visíveis|
|[CA2112](../code-quality/ca2112.md)|Tipos protegidos não devem expor campos|
|[CA2114](../code-quality/ca2114.md)|A segurança do método deve ser um superconjunto do tipo|
|[CA2115](../code-quality/ca2115.md)|Chamar GC.KeepAlive ao usar recursos nativos|
|[CA2116](../code-quality/ca2116.md)|Métodos APTCA devem chamar somente métodos APTCA|
|[CA2117](../code-quality/ca2117.md)|Tipos APTCA devem estender somente tipos base APTCA|
|[CA2118](../code-quality/ca2118.md)|Examinar o uso de SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119.md)|Selar métodos que atendem a interfaces particulares|
|[CA2120](../code-quality/ca2120.md)|Construtores de serialização seguros|
|[CA2121](../code-quality/ca2121.md)|Construtores estáticos devem ser particulares|
|[CA2122](../code-quality/ca2122.md)|Não expor indiretamente métodos com demandas de link|
|[CA2123](../code-quality/ca2123.md)|As demandas de link de substituição devem ser idênticas à base|
|[CA2124](../code-quality/ca2124.md)|Encapsular cláusulas finally vulneráveis em try externo|
|[CA2126](../code-quality/ca2126.md)|As demandas de link de tipo exigem demandas de herança|
|[CA2130](../code-quality/ca2130.md)|Constantes críticas de segurança devem ser transparentes|
|[CA2131](../code-quality/ca2131.md)|Tipos críticos de segurança podem não participar da equivalência de tipo|
|[CA2132](../code-quality/ca2132.md)|Construtores padrão devem ser pelo menos tão críticos quanto construtores padrão do tipo base|
|[CA2133](../code-quality/ca2133.md)|Representantes devem ser associados a métodos com transparência consistente|
|[CA2134](../code-quality/ca2134.md)|Os métodos devem manter uma transparência consistente durante a substituição dos métodos base|
|[CA2135](../code-quality/ca2135.md)|Os assemblies de nível 2 não devem conter LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Membros não devem ter anotações de transparência conflitantes|
|[CA2137](../code-quality/ca2137.md)|Métodos transparentes devem conter apenas a IL verificável|
|[CA2138](../code-quality/ca2138.md)|Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139.md)|Métodos transparentes podem não usar o atributo HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140.md)|O código transparente não deve referenciar itens críticos de segurança|
|[CA2141](../code-quality/ca2141.md)|Métodos transparentes não devem satisfazer LinkDemands|
|[CA2142](../code-quality/ca2142.md)|O código transparente não deve ser protegido com LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Métodos transparentes não devem usar demandas de segurança|
|[CA2144](../code-quality/ca2144.md)|O código transparente não deve carregar assemblies de matrizes de bytes|
|[CA2145](../code-quality/ca2145.md)|Métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146.md)|Os tipos devem ser pelo menos tão críticos quanto seus tipos base e interfaces|
|[CA2147](../code-quality/ca2147.md)|Métodos transparentes podem não usar declarações de segurança|
|[CA2149](../code-quality/ca2149.md)|Métodos transparentes não devem chamar código nativo|
|[CA2210](../code-quality/ca2210.md)|Assemblies devem ter nomes fortes válidos|
|[CA2300](ca2300.md)|Não usar o desserializador BinaryFormatter não seguro|
|[CA2301](ca2301.md)|Não chamar BinaryFormatter.Deserialize sem antes definir BinaryFormatter.Binder|
|[CA2302](ca2302.md)|Verificar se o BinaryFormatter.Binder está definido antes de chamar BinaryFormatter.Deserialize|
|[CA2305](ca2305.md)|Não usar o desserializador inseguro LosFormatter|
|[CA2310](ca2310.md)|Não usar o desserializador inseguro NetDataContractSerializer|
|[CA2311](ca2311.md)|Não desserializar sem definir primeiro NetDataContractSerializer.Binder|
|[CA2312](ca2312.md)|Verificar se NetDataContractSerializer.Binder foi definido antes de desserializar|
|[CA2315](ca2315.md)|Não usar o desserializador inseguro ObjectStateFormatter|
|[CA2321](ca2321.md)|Não desserializar com JavaScriptSerializer usando um SimpleTypeResolver|
|[CA2322](ca2322.md)|Garantir que o JavaScriptSerializer não seja inicializado com SimpleTypeResolver antes de desserializar|
|[CA3001](../code-quality/ca3001.md)|Examinar código quanto a vulnerabilidades de injeção de SQL|
|[CA3002](../code-quality/ca3002.md)|Examinar código quanto a vulnerabilidades de XSS|
|[CA3003](../code-quality/ca3003.md)|Examinar código quanto a vulnerabilidades de injeção de caminho|
|[CA3004](../code-quality/ca3004.md)|Examinar código quanto a vulnerabilidades de divulgação de informações|
|[CA3005](../code-quality/ca3005.md)|Examinar código quanto a vulnerabilidades de injeção de LDAP|
|[CA3006](../code-quality/ca3006.md)|Examinar código quanto a vulnerabilidades de injeção de comando de processo|
|[CA3007](../code-quality/ca3007.md)|Examinar código quanto a vulnerabilidades de redirecionamento aberto|
|[CA3008](../code-quality/ca3008.md)|Examinar código quanto a vulnerabilidades de injeção de XPath|
|[CA3009](../code-quality/ca3009.md)|Examinar código quanto a vulnerabilidades de injeção de XML|
|[CA3010](../code-quality/ca3010.md)|Examinar código quanto a vulnerabilidades de injeção de XAML|
|[CA3011](../code-quality/ca3011.md)|Examinar código quanto a vulnerabilidades de injeção de DLL|
|[CA3012](../code-quality/ca3012.md)|Examinar código quanto a vulnerabilidades de injeção de regex|
|[CA5358](../code-quality/ca5358.md)|Não usar modos de criptografia não seguros|
|[CA5403](../code-quality/ca5403.md)|Não embutir o certificado em código|
