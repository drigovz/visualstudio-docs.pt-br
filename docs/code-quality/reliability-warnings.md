---
title: Regras de confiabilidade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a35b9c49f2eb5655eeb67721b0fafdbbe1e087
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808266"
---
# <a name="reliability-rules"></a>Regras de confiabilidade

As regras de confiabilidade dão suporte à confiabilidade de aplicativo e biblioteca, como a memória correta e o uso de thread.

|Regra|Descrição|
|----------|-----------------|
|[CA2000: Descartar objetos antes de perder o escopo](../code-quality/ca2000.md)|Como pode ocorrer um evento excepcional que impedirá a execução do finalizador de um objeto, o objeto deve ser explicitamente descartado antes que todas as referências a ele estejam fora do escopo.|
|[CA2002: Não bloquear objetos com identidade fraca](../code-quality/ca2002.md)|Diz-se que um objeto tem uma identidade fraca quando puder ser acessado diretamente em todos os limites de domínio do aplicativo. Um thread que tente adquirir um bloqueio em um objeto com uma identidade fraca pode ser bloqueado por um segundo thread em um domínio de aplicativo diferente com um bloqueio no mesmo objeto.|
|[CA2007: não aguardar diretamente uma tarefa](../code-quality/ca2007.md)|Um método assíncrono [aguarda](/dotnet/csharp/language-reference/keywords/await) um <xref:System.Threading.Tasks.Task> diretamente.|
|[CA2008: Não criar tarefas sem passar um TaskScheduler](../code-quality/ca2008.md)|Uma operação de criação ou de continuação de tarefa usa uma sobrecarga de método que não especifica um <xref:System.Threading.Tasks.TaskScheduler> parâmetro.|
|[CA2009: Não chamar ToImmutableCollection em um valor ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable` o método não era necessariamente chamado em uma coleção imutável do <xref:System.Collections.Immutable> namespace.|
|[CA2011: Não atribuir a propriedade em seu próprio setter](../code-quality/ca2011.md) | Uma propriedade recebeu acidentalmente um valor dentro de seu próprio [acessador set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
|[CA2012: Usar ValueTasks corretamente](../code-quality/ca2012.md) | ValueTasks retornados de invocações de membro devem ser diretamente aguardados.  Tenta consumir um ValueTask várias vezes ou para acessar diretamente um resultado antes que seja conhecido a ser concluído pode resultar em uma exceção ou corrupção.  Ignorar essa ValueTask é provavelmente uma indicação de um bug funcional e pode prejudicar o desempenho. |
|[CA2013: Não usar ReferenceEquals com tipos de valor](../code-quality/ca2013.md) | Ao comparar valores usando <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , se objA e objB forem tipos de valor, eles estarão em caixa antes de serem passados para o <xref:System.Object.ReferenceEquals%2A> método. Isso significa que, mesmo que objA e objB representem a mesma instância de um tipo de valor, o método, no <xref:System.Object.ReferenceEquals%2A> entanto, retorna false. |
|[CA2014: não use stackalloc em loops.](../code-quality/ca2014.md) | O espaço de pilha alocado por um stackalloc é liberado apenas no final da invocação do método atual.  Usá-lo em um loop pode resultar em aumento de pilha não associado e condições de estouro de pilha eventual. |
|[CA2015: não definir finalizadores para tipos derivados de MemoryManager &lt; T&gt;](../code-quality/ca2015.md) | Adicionar um finalizador a um tipo derivado de <xref:System.Buffers.MemoryManager%601> pode permitir que a memória seja liberada enquanto ainda estiver em uso por um <xref:System.Span%601> . |
|[CA2016: Encaminhe o parâmetro CancellationToken para os métodos que recebem um](ca2016.md) | Encaminhe o `CancellationToken` parâmetro para os métodos que usam um para garantir que as notificações de cancelamento da operação sejam propagadas corretamente ou repassem `CancellationToken.None` explicitamente para indicar, de forma intencional, não a propagação do token. |
