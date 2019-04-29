---
title: Regras de análise de código CA2153 para exceções de estado corrompido
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542151"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitar manipular exceções de estado corrompido

|||
|-|-|
|NomeDoTipo|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

[Exceções de estado corrompidas (CSEs)](https://msdn.microsoft.com/magazine/dd419661.aspx) indicam que a memória corrupção existe em seu processo. Capturar esses em vez de permitir que o processo falhe pode levar a vulnerabilidades de segurança se um invasor pode colocar uma exploração para a região de memória corrompida.

## <a name="rule-description"></a>Descrição da regra

CSE indica que o estado de um processo foi corrompido e não capturado pelo sistema. No cenário de estado corrompido, um manipulador geral só captura a exceção se você marcar o método com o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> atributo. Por padrão, o [Common Language Runtime (CLR)](/dotnet/standard/clr) não invoca manipuladores catch para CSEs.

A opção mais segura é permitir que o processo falhe sem capturar esses tipos de exceções. Até mesmo código de registro pode permitir que os invasores podem explorar os bugs de corrupção de memória.

Esse aviso dispara quando capturando CSEs com um manipulador geral que captura todas as exceções, por exemplo, `catch (System.Exception e)` ou `catch` sem nenhum parâmetro de exceção.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para resolver este aviso, siga um destes procedimentos:

- Remover o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo. Isso será revertido para o comportamento de tempo de execução padrão no qual os CSEs não são passados para manipuladores catch.

- Remova o manipulador catch geral in preference of manipuladores que capturar tipos de exceção específica. Isso pode incluir CSEs, supondo que o código do manipulador possa tratá-las com segurança (raro).

- Relançar a CSE no manipulador catch, que passa a exceção para o chamador e deve resultar no encerramento do processo em execução.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de pseudocódigo

### <a name="violation"></a>Violação

O pseudocódigo a seguir ilustra o padrão detectado por essa regra.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Solução 1: remover o atributo

Removendo o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo garante que as exceções de estado corrompido não são manipuladas pelo seu método.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Solução 2: capturar exceções específicas

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
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Solução 3: relançar

Relançar a exceção.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```