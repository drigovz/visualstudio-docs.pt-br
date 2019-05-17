---
title: 'CA2000: Descartar objetos antes de perder o escopo'
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 732b3d683802c50042ee40fee1549a9d247e2470
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804971"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Descartar objetos antes de perder o escopo

|||
|-|-|
|NomeDoTipo|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um objeto de local de um <xref:System.IDisposable> tipo é criado, mas o objeto não for descartado antes de todas as referências ao objeto estão fora do escopo.

## <a name="rule-description"></a>Descrição da regra

Se um objeto descartável não for explicitamente descartado antes de todas as referências a ele estejam fora do escopo, o objeto será descartado em algum momento indeterminado quando o coletor de lixo execute o finalizador do objeto. Como pode ocorrer um evento excepcional que impedirá que o finalizador do objeto seja executado, o objeto deve ser explicitamente descartado.

### <a name="special-cases"></a>Casos especiais

A regra CA2000 não é acionado para objetos dos seguintes tipos de locais, mesmo se o objeto não for descartado:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Passando um objeto de um desses tipos para um construtor e, em seguida, atribuí-la a um campo indicam um *dispose de transferência de propriedade* para o tipo construído recentemente. Ou seja, o tipo construído recentemente agora é responsável pelo descarte do objeto. Se seu código passa um objeto de um desses tipos para um construtor, nenhuma violação de regra CA2000 ocorre mesmo se o objeto não for descartado antes de todas as referências a ele estão fora do escopo.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, chame <xref:System.IDisposable.Dispose%2A> no objeto antes de todas as referências a ele estejam fora do escopo.

Você pode usar o [ `using` instrução](/dotnet/csharp/language-reference/keywords/using-statement) ([ `Using` ](/dotnet/visual-basic/language-reference/statements/using-statement) no Visual Basic) para encapsular os objetos que implementam <xref:System.IDisposable>. Objetos que são encapsulados em dessa maneira são descartados automaticamente no final do `using` bloco. No entanto, as situações a seguir não devem ou não podem ser tratadas com uma `using` instrução:

- Para retornar um objeto descartável, o objeto deve construído em uma `try/finally` bloquear fora de um `using` bloco.

- Não inicializar membros de um objeto descartável no construtor de uma `using` instrução.

- Quando os construtores que são protegidos pelo manipulador de exceção apenas um estão aninhados na [parte de aquisição de um `using` instrução](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), uma falha no construtor externa pode resultar no objeto criado pelo construtor aninhado nunca que está sendo fechado. No exemplo a seguir, uma falha na <xref:System.IO.StreamReader> construtor pode resultar no <xref:System.IO.FileStream> objeto nunca seja fechada. CA2000 sinaliza uma violação da regra nesse caso.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Objetos dinâmicos devem usar um objeto de sombra para implementar o padrão de descarte de <xref:System.IDisposable> objetos.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra, a menos que:

- Chamei um método em seu objeto que chama `Dispose`, tais como <xref:System.IO.Stream.Close%2A>
- O método que gerou o aviso retorna um <xref:System.IDisposable> objeto que encapsula o objeto
- O método de alocação não tem propriedade dispose; ou seja, a responsabilidade de descartar o objeto é transferida para outro objeto ou wrapper que criou no método e retornado ao chamador

## <a name="related-rules"></a>Regras relacionadas

- [CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202: Não descartar objetos várias vezes](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Exemplo

Se você estiver implementando um método que retorna um objeto descartável, use um bloco try/finally sem um bloco catch para certificar-se de que o objeto é descartado. Ao usar um bloco try/finally, você pode permitir que exceções a ser gerado no ponto de falha e certifique-se de que o objeto é descartado.

No método OpenPort1, a chamada para abrir o objeto ISerializable SerialPort ou a chamada ao SomeMethod pode falhar. Um aviso CA2000 é gerado dessa implementação.

No método OpenPort2, dois objetos de SerialPort são declarado e está definida como null:

- `tempPort`, que é usado para testar as operações do método tenha êxito.

- `port`, que é usado para o valor retornado do método.

O `tempPort` é criado e aberto em um `try` bloco e qualquer outro necessários o trabalho é executado no mesmo `try` bloco. No final do `try` bloco, a porta aberta é atribuído para o `port` objeto que será retornado e o `tempPort` objeto é definido como `null`.

O `finally` bloco verifica o valor de `tempPort`. Se não for nulo, uma operação no método tiver falhado, e `tempPort` está fechado para certificar-se de que todos os recursos são liberados. O objeto de porta retornada conterá o objeto de SerialPort aberto se as operações do método foi bem-sucedida, ou ele será nulo se uma operação falhou.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function

Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If

   End Try

   Return port

End Function
```

## <a name="example"></a>Exemplo

Por padrão, o compilador do Visual Basic tem todos os operadores aritméticos a verificação de estouro. Portanto, qualquer operação aritmética de Visual Basic pode lançar uma <xref:System.OverflowException>. Isso pode levar a inesperado violações de regras como CA2000. Por exemplo, a seguinte função CreateReader1 produzirá uma violação de CA2000, porque o compilador do Visual Basic está emitindo um instrução para a adição que poderia lançar uma exceção que faria com que o StreamReader para não ser descartado de verificação de estouro.

Para corrigir isso, você pode desabilitar a emissão de verificações de estouro pelo compilador do Visual Basic em seu projeto ou você pode modificar seu código como a seguinte função CreateReader2.

Para desabilitar a emissão de verificações de estouro, o nome do projeto no Gerenciador de soluções com o botão direito e, em seguida, clique em **propriedades**. Clique em **Compile**, clique em **opções avançadas de compilação**e, em seguida, marque **remover verificações de estouro de inteiro**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable>
- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)