---
title: 'CA2153: Evitar tratamento de exceções de estado corrompido'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3e8253936c406a3f84304337b818e0f28f1036f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950897"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitar tratamento de exceções de estado corrompido

|||
|-|-|
|NomeDoTipo|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

[Corrompido exceções de estado (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) indicam que a memória corrupção existe em seu processo. Capturar esses em vez de permitir que o processo falhe pode levar a vulnerabilidades de segurança se um invasor pode colocar uma exploração para a região de memória corrompida.

## <a name="rule-description"></a>Descrição da regra

CSE indica que o estado de um processo foi corrompido e não capturado pelo sistema. No cenário de estado corrompido, um manipulador geral só captura a exceção se você marcar o método com as devidas `HandleProcessCorruptedStateExceptions` atributo. Por padrão, o [Common Language Runtime (CLR)](/dotnet/standard/clr) não invoca manipuladores catch para CSEs.

Permitindo que o processo falhe sem capturar esses tipos de exceções é a opção mais segura, como o mesmo código de registro pode permitir que os invasores podem explorar os bugs de corrupção de memória.

Esse aviso dispara quando capturando CSEs com um manipulador geral que captura todas as exceções, como catch (Exception) ou catch (especificação de exceção).

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para resolver este aviso, siga um destes procedimentos:

- Remover o `HandleProcessCorruptedStateExceptions` atributo. Isso será revertido para o comportamento de tempo de execução padrão no qual os CSEs não são passados para manipuladores catch.

- Remova o manipulador catch geral in preference of manipuladores que capturar tipos de exceção específica. Isso pode incluir CSEs, supondo que o código do manipulador possa tratá-las com segurança (raro).

- Relançar a CSE no manipulador catch, que garante que a exceção é passada para o chamador e resultarão no encerramento do processo em execução.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de pseudocódigo

### <a name="violation"></a>Violação

O pseudocódigo a seguir ilustra o padrão detectado por essa regra.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Solução 1

Removendo o atributo HandleProcessCorruptedExceptions garante que as exceções não ocorrerão.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Solução 2

Remover o manipulador catch geral e capturar apenas os tipos de exceção específica.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Solução 3

Relançar a exceção.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```