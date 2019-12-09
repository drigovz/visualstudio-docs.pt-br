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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 602f372e11c4a9a8506186535958fc4f22da7806
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649112"
---
# <a name="reliability-warnings"></a>Avisos de confiabilidade

Os avisos de confiabilidade dão suporte à biblioteca e confiabilidade do aplicativo, como a memória correta e o uso do thread. As regras de confiabilidade incluem:

|Regra|Descrição|
|----------|-----------------|
|[CA2000: descartar objetos antes de perder o escopo](../code-quality/ca2000.md)|Como pode ocorrer um evento excepcional que impedirá a execução do finalizador de um objeto, o objeto deve ser explicitamente descartado antes que todas as referências a ele estejam fora do escopo.|
|[CA2001: evitar chamar métodos problemáticos](../code-quality/ca2001.md)|Um membro chama um método potencialmente perigoso ou problemático.|
|[CA2002: não bloquear objetos com identidade fraca](../code-quality/ca2002.md)|Diz-se que um objeto tem uma identidade fraca quando puder ser acessado diretamente em todos os limites de domínio do aplicativo. Um thread que tente adquirir um bloqueio em um objeto com uma identidade fraca pode ser bloqueado por um segundo thread em um domínio de aplicativo diferente com um bloqueio no mesmo objeto.|
|[CA2003: não tratar fibras como threads](../code-quality/ca2003.md)|Um thread gerenciado está sendo tratado como um Thread Win32.|
|[CA2004: remover chamadas para GC.KeepAlive](../code-quality/ca2004.md)|Se você estiver convertendo para uso de SafeHandle, remova todas as chamadas para GC. KeepAlive (objeto). Nesse caso, as classes não devem ter que chamar GC. KeepAlive, supondo que eles não tenham um finalizador, mas dependem de SafeHandle para finalizar o identificador do sistema operacional para eles.|
|[CA2006: use SafeHandle para encapsular recursos nativos](../code-quality/ca2006.md)|O uso de IntPtr em código gerenciado pode indicar um problema de segurança e confiabilidade em potencial. Todos os usos de IntPtr devem ser examinados para determinar se o uso de um SafeHandle, ou tecnologia semelhante, é necessário em seu lugar.|
|[CA2007: não aguardando diretamente uma tarefa](../code-quality/ca2007.md)|Um método assíncrono [aguarda](/dotnet/csharp/language-reference/keywords/await) um <xref:System.Threading.Tasks.Task> diretamente.|
