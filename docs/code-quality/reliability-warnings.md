---
title: Avisos de confiabilidade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74c1a5202b05b3ffe6f9b6c5b24804fb259287c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825332"
---
# <a name="reliability-warnings"></a>Avisos de confiabilidade
Avisos de confiabilidade dão suporte a confiabilidade de biblioteca e o aplicativo, como o uso de memória e thread corretos.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA2000: Descartar objetos antes de perder escopo](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Como pode ocorrer um evento excepcional que impedirá a execução do finalizador de um objeto, o objeto deve ser explicitamente descartado antes que todas as referências a ele estejam fora do escopo.|
|[CA2001: Evite chamar métodos problemáticos](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Um membro chama um método potencialmente perigoso ou problemático.|
|[CA2002: Não bloquear objetos com identidade fraca](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Diz-se que um objeto tem uma identidade fraca quando puder ser acessado diretamente em todos os limites de domínio do aplicativo. Um thread que tente adquirir um bloqueio em um objeto com uma identidade fraca pode ser bloqueado por um segundo thread em um domínio de aplicativo diferente com um bloqueio no mesmo objeto.|
|[CA2003: Não trate fibras como threads](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Um thread gerenciado está sendo tratado como um thread do Win32.|
|[CA2004: Remova chamadas para GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Se você estiver convertendo para o uso de SafeHandle, remova todas as chamadas para GC. KeepAlive (object). Nesse caso, as classes não deve chamar GC. Manipular KeepAlive, supondo que eles não têm um finalizador, mas dependam de SafeHandle para finalizar o sistema operacional para eles.|
|[CA2006: Use SafeHandle para encapsular recursos nativos](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|O uso de IntPtr em código gerenciado pode indicar um problema de segurança e confiabilidade em potencial. Todos os usos de IntPtr devem ser examinados para determinar se o uso de um SafeHandle, ou tecnologia semelhante, é necessário em seu lugar.|