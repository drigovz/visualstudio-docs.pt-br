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
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252590"
---
# <a name="reliability-warnings"></a>Avisos de confiabilidade

Os avisos de confiabilidade dão suporte à biblioteca e confiabilidade do aplicativo, como a memória correta e o uso do thread. As regras de confiabilidade incluem:

|Regra|Descrição|
|----------|-----------------|
|[CA2000: Descartar objetos antes de perder o escopo @ no__t-0|Como pode ocorrer um evento excepcional que impedirá a execução do finalizador de um objeto, o objeto deve ser explicitamente descartado antes que todas as referências a ele estejam fora do escopo.|
|[CA2001: Evite chamar métodos problemáticos @ no__t-0|Um membro chama um método potencialmente perigoso ou problemático.|
|[CA2002: Não bloquear objetos com identidade fraca @ no__t-0|Diz-se que um objeto tem uma identidade fraca quando puder ser acessado diretamente em todos os limites de domínio do aplicativo. Um thread que tente adquirir um bloqueio em um objeto com uma identidade fraca pode ser bloqueado por um segundo thread em um domínio de aplicativo diferente com um bloqueio no mesmo objeto.|
|[CA2003: Não tratar fibras como threads @ no__t-0|Um thread gerenciado está sendo tratado como um Thread Win32.|
|[CA2004: Remova as chamadas para GC. KeepAlive @ no__t-0|Se você estiver convertendo para uso de SafeHandle, remova todas as chamadas para GC. KeepAlive (objeto). Nesse caso, as classes não devem ter que chamar GC. KeepAlive, supondo que eles não tenham um finalizador, mas dependem de SafeHandle para finalizar o identificador do sistema operacional para eles.|
|[CA2006: Usar o SafeHandle para encapsular recursos nativos @ no__t-0|O uso de IntPtr em código gerenciado pode indicar um problema de segurança e confiabilidade em potencial. Todos os usos de IntPtr devem ser examinados para determinar se o uso de um SafeHandle, ou tecnologia semelhante, é necessário em seu lugar.|
|[CA2007: Não aguardar diretamente uma tarefa @ no__t-0|Um método assíncrono [aguarda](/dotnet/csharp/language-reference/keywords/await) um <xref:System.Threading.Tasks.Task> diretamente.|
