---
title: Conjunto de regras recomendadas gerenciado para código gerenciado
ms.date: 11/04/2016
description: Saiba mais sobre a regra de regras recomendadas gerenciadas no Visual Studio. Veja descrições das regras que se concentram na segurança, robustez e outros problemas críticos.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e691e6dc48b33ff00f6824436b80e5f49721db98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867900"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Conjunto de regras recomendadas gerenciado para código gerenciado

Use a regra de regras recomendadas gerenciadas pela Microsoft para se concentrar nos problemas mais críticos em seu código gerenciado, incluindo possíveis falhas de segurança, falhas de aplicativo e outros erros importantes de lógica e de design. Esse conjunto de regras inclui todas as regras no conjunto de regras de [regras mínimas gerenciadas](managed-minimum-rules-rule-set-for-managed-code.md) .

Inclua esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para seus projetos.

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
