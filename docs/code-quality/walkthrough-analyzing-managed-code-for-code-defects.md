---
title: Walkthrough analisando código gerenciado para defeitos de código | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab1e0b890d6241742770ed38ff61fc1c2c0ed2f4
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535696"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Walkthrough: usar a análise de código estático para encontrar defeitos de código

Neste tutorial, você analisará um projeto gerenciado para defeitos de código usando a análise de código herdada.

Este artigo orienta você pelo processo de uso da análise herdada para analisar seus assemblies de código gerenciado .NET para conformidade com as diretrizes de design do .NET.

## <a name="create-a-class-library"></a>Criar uma biblioteca de classes

1. Abra o Visual Studio e crie um novo projeto do modelo **biblioteca de classes (.NET Framework)** .

1. Nomeie o projeto **CodeAnalysisManagedDemo**.

1. Depois que o projeto for criado, abra o arquivo *Class1.cs* .

1. Substitua o texto existente em Class1.cs pelo seguinte código:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Salve o arquivo Class1.cs.

## <a name="analyze-the-project-for-code-defects"></a>Analisar o projeto para defeitos de código

1. Selecione o projeto CodeAnalysisManagedDemo em **Gerenciador de soluções**.

2. No menu **Projeto**, clique em **Propriedades**.

   A página de propriedades CodeAnalysisManagedDemo é exibida.

3. Escolha a guia **análise de código** .

::: moniker range="vs-2017"

4. Verifique se **Habilitar análise de código no Build** está selecionado.

5. Na lista suspensa **executar esta regra definida** , selecione **todas as regras da Microsoft**.

::: moniker-end

::: moniker range=">=vs-2019"

4. Verifique se **executar na compilação** está selecionado na seção **analisadores binários** .

5. Na lista suspensa **regras ativas** , selecione **Microsoft All Rules**.

::: moniker-end

6. No menu **arquivo** , clique em **salvar itens selecionados**e feche as páginas de propriedades.

7. No menu **Compilar** , clique em **criar CodeAnalysisManagedDemo**.

    Os avisos de compilação do projeto CodeAnalysisManagedDemo são mostrados nas janelas de **lista de erros** e **saída** .

## <a name="correct-the-code-analysis-issues"></a>Corrigir os problemas de análise de código

1. No menu **Exibir** , escolha **lista de erros**.

    Dependendo do perfil de desenvolvedor que você escolheu, talvez seja necessário apontar para **outras janelas** no menu **Exibir** e, em seguida, escolher **lista de erros**.

1. Em **Gerenciador de soluções**, escolha **Mostrar todos os arquivos**.

1. Expanda o nó Propriedades e, em seguida, abra o arquivo *AssemblyInfo.cs* .

1. Use as seguintes dicas para corrigir os avisos:

   [CA1014: Marcar assemblies com o CLSCompliantAttribute](../code-quality/ca1014.md): Adicione o código `[assembly: CLSCompliant(true)]` ao final do arquivo AssemblyInfo.cs.

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032.md): Adicione o Construtor `public demo (String s) : base(s) { }` à classe `demo`.

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032.md): Adicione o Construtor `public demo (String s, Exception e) : base(s, e) { }` à classe `demo`.

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032.md): Adicione o Construtor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` à demonstração da classe. Você também precisará adicionar uma instrução `using` para <xref:System.Runtime.Serialization?displayProperty=fullName>.

   [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032.md): Adicione o Construtor `public demo () : base() { }` à classe `demo`.

   [CA1709: os identificadores devem estar em maiúsculas](../code-quality/ca1709.md)/minúsculas: altere a capitalização do namespace `testCode` para `TestCode`.

   [CA1709: os identificadores devem estar em maiúsculas e minúsculas](../code-quality/ca1709.md): altere o nome do membro para `Demo`.

   [CA1709: os identificadores devem estar em maiúsculas e minúsculas](../code-quality/ca1709.md): altere o nome do membro para `Item`.

   [CA1710: os identificadores devem ter o sufixo correto](../code-quality/ca1710.md): altere o nome da classe e seus construtores para `DemoException`.

   [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237.md): Adicione o atributo `[Serializable ()]` à classe `demo`.

   [CA2210: assemblies devem ter nomes fortes válidos](../code-quality/ca2210.md): assinar ' CodeAnalysisManagedDemo ' com uma chave de nome forte:

   1. No menu **projeto** , escolha **CodeAnalysisManagedDemo Propriedades**.

      As propriedades do projeto são exibidas.

   1. Escolha a guia **Assinatura**.

   1. Marque a caixa de seleção **assinar o assembly** .

   1. Na lista **escolher um arquivo de chave de nome de cadeia de caracteres** , selecione **\<New >** .

      A caixa de diálogo **criar chave de nome forte** é exibida.

   1. Para **nome de arquivo de chave**, insira **TestKey**.

   1. Insira uma senha e escolha **OK**.

   1. No menu **arquivo** , escolha **salvar itens selecionados**e feche as páginas de propriedades.

   Depois de concluir todas as alterações, o arquivo Class1.cs deverá ser semelhante ao seguinte:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Recompilar o projeto.

## <a name="exclude-code-analysis-warnings"></a>Excluir avisos de análise de código

1. Para cada um dos avisos restantes, faça o seguinte:

    1. Selecione o aviso no **lista de erros**.

    1. No menu do clique com o botão direito do mouse (menu de contexto), escolha **suprimir** > **no arquivo de supressão**.

1. Recompilar o projeto.

     O projeto é compilado sem avisos ou erros.

## <a name="see-also"></a>Consulte também

[Análise de código para código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md)
