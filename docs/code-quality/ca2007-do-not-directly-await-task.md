---
title: 'CA2007: Não diretamente espera uma tarefa'
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: 8e94b67d1924e2144f658cd6bcd5989751efdb85
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699675"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Não diretamente espera uma tarefa

|||
|-|-|
|NomeDoTipo|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um método assíncrono [awaits](/dotnet/csharp/language-reference/keywords/await) um <xref:System.Threading.Tasks.Task> diretamente.

## <a name="rule-description"></a>Descrição da regra

Quando um método assíncrono aguarda um <xref:System.Threading.Tasks.Task> diretamente, a continuação ocorre no mesmo thread que criou a tarefa. Esse comportamento pode ser dispendioso em termos de desempenho e pode resultar em um deadlock no thread da interface do usuário. Considere a possibilidade de chamar <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> para sinalizar sua intenção de continuação.

Esta regra foi introduzida com o [analisadores FxCop](install-fxcop-analyzers.md) e não existe no "herdados" (análise de código estático) FxCop.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir violações, chame <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> sobre o aguardada <xref:System.Threading.Tasks.Task>. Você pode transmitir `true` ou `false` para o `continueOnCapturedContext` parâmetro.

- Chamando `ConfigureAwait(true)` na tarefa tem o mesmo comportamento que não explicitamente chamando <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. Explicitamente chamando esse método, você está permitindo que os leitores sabe que deseja executar a continuação no contexto de sincronização original intencionalmente.

- Chamar `ConfigureAwait(false)` na tarefa de programar continuações para o pool de threads, evitando assim um deadlock no thread da interface do usuário. Passando `false` é uma boa opção para bibliotecas de aplicativo independente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Você pode suprimir esse aviso se você souber que o consumidor não é um aplicativo de GUI (interface) do usuário gráfica ou se o consumidor não tiver um <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Exemplo

O trecho de código a seguir gera o aviso:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Para corrigir a violação, chame <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> sobre o aguardada <xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="see-also"></a>Consulte também

- [Eu deve aguardar uma tarefa com ConfigureAwait (False)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Instalar analisadores FxCop no Visual Studio](install-fxcop-analyzers.md)