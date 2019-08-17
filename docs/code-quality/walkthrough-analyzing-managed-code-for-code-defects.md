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
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548005"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Passo a passo: Usar a análise de código estático para encontrar defeitos de código

Neste tutorial, você analisará um projeto gerenciado para defeitos de código usando a análise de código herdada.

Este artigo orienta você pelo processo de uso da análise herdada para analisar seus assemblies de código gerenciado .NET para conformidade com as diretrizes de design do .NET.

## <a name="create-a-class-library"></a>Criar uma biblioteca de classes

### <a name="to-create-a-class-library"></a>Para criar uma biblioteca de classes

1. No menu **Arquivo**, escolha **Novo** > **Projeto**.

1. Na caixa de diálogo **novo projeto** , expanda o**Visual C#**  **instalado** > e, em seguida, escolha **Windows Desktop**.

1. Escolha o modelo de **biblioteca de classes (.NET Framework)** .

1. Na caixa de texto **nome** , digite **CodeAnalysisManagedDemo** e clique em **OK**.

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

## <a name="analyze-the-project"></a>Analisar o projeto

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analisar um projeto gerenciado para defeitos de código

1. Selecione o projeto CodeAnalysisManagedDemo em **Gerenciador de soluções**.

1. No menu **Projeto**, clique em **Propriedades**.

     A página de propriedades CodeAnalysisManagedDemo é exibida.

1. Escolha a guia **análise de código** .

1. Verifique se a opção **Habilitar análise de código no Build** está marcada.

1. Na lista suspensa **executar esta regra definida** , selecione **todas as regras da Microsoft**.

1. No menu **arquivo** , clique em **salvar itens selecionados**e feche as páginas de propriedades.

1. No menu **Compilar** , clique em **criar CodeAnalysisManagedDemo**.

    Os avisos de compilação do projeto CodeAnalysisManagedDemo são mostrados nas janelas de **lista de erros** e **saída** .

## <a name="correct-the-code-analysis-issues"></a>Corrigir os problemas de análise de código

### <a name="to-correct-code-analysis-rule-violations"></a>Para corrigir violações de regra de análise de código

1. No menu **Exibir** , escolha **lista de erros**.

    Dependendo do perfil de desenvolvedor que você escolheu, talvez seja necessário apontar para **outras janelas** no menu **Exibir** e, em seguida, escolher **lista de erros**.

1. Em **Gerenciador de soluções**, escolha **Mostrar todos os arquivos**.

1. Expanda o nó Propriedades e, em seguida, abra o arquivo *AssemblyInfo.cs* .

1. Use as seguintes dicas para corrigir os avisos:

   [CA1014: Marcar assemblies com o](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)CLSCompliantAttribute: Microsoft. Design: ' demo ' deve ser marcado com o CLSCompliantAttribute e seu valor deve ser true.

   1. Adicione o código `using System;` ao arquivo AssemblyInfo.cs.

   1. Em seguida, adicione o `[assembly: CLSCompliant(true)]` código ao final do arquivo AssemblyInfo.cs.

   [CA1032: Implementar construtores](../code-quality/ca1032-implement-standard-exception-constructors.md)de exceção padrão: Microsoft.Design: Adicione o seguinte construtor a esta classe: demonstração pública (cadeia de caracteres)

   1. Adicione o construtor `public demo (String s) : base(s) { }` à classe. `demo`

   [CA1032: Implementar construtores](../code-quality/ca1032-implement-standard-exception-constructors.md)de exceção padrão: Microsoft.Design: Adicione o seguinte construtor a esta classe: demonstração pública (cadeia de caracteres, exceção)

   1. Adicione o construtor `public demo (String s, Exception e) : base(s, e) { }` à classe. `demo`

   [CA1032: Implementar construtores](../code-quality/ca1032-implement-standard-exception-constructors.md)de exceção padrão: Microsoft.Design: Adicione o seguinte construtor a esta classe: demonstração protegida (SerializationInfo, StreamingContext)

   1. Adicione o código `using System.Runtime.Serialization;` ao início do arquivo Class1.cs.

   1. Em seguida, adicione o Construtor`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementar construtores](../code-quality/ca1032-implement-standard-exception-constructors.md)de exceção padrão: Microsoft.Design: Adicione o seguinte construtor a esta classe: demonstração pública ()

   1. Adicione o construtor `public demo () : base() { }` à classe `demo` **.**

   [CA1709: Os identificadores devem estar em](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)maiúsculas/minúsculas: Microsoft.Naming: Corrija a capitalização do nome de namespace ' testCode ' alterando-o para ' TestCode '.

   1. Altere a capitalização do namespace `testCode` para `TestCode`.

   [CA1709: Os identificadores devem estar em](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)maiúsculas/minúsculas: Microsoft.Naming: Corrija a capitalização do nome de tipo ' demo ' alterando-a para ' demo '.

   1. Altere o nome do membro para `Demo`.

   [CA1709: Os identificadores devem estar em](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)maiúsculas/minúsculas: Microsoft.Naming: Corrija a capitalização do nome de membro ' item ' alterando-o para ' item '.

   1. Altere o nome do membro para `Item`.

   [CA1710: Os identificadores devem ter o](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)sufixo correto: Microsoft.Naming: Renomeie ' testCode. demo ' para terminar em ' Exception '.

   1. Altere o nome da classe e seus construtores para `DemoException`.

   [CA2210: Os assemblies devem ter nomes](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)fortes válidos: Assine ' CodeAnalysisManagedDemo ' com uma chave de nome forte.

   1. No menu **projeto** , escolha **CodeAnalysisManagedDemo Propriedades**.

      As propriedades do projeto são exibidas.

   1. Escolha a guia **Assinatura**.

   1. Marque a caixa de seleção **assinar o assembly** .

   1. Na lista **escolher um arquivo de chave de nome de cadeia de caracteres** , selecione  **\<novo... >** .

      A caixa de diálogo **criar chave de nome forte** é exibida.

   1. No **nome do arquivo de chave**, digite TestKey.

   1. Insira uma senha e escolha **OK**.

   1. No menu **arquivo** , escolha **salvar itens selecionados**e feche as páginas de propriedades.

   [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: Adicione um atributo [Serializable] ao tipo ' demo ', pois esse tipo implementa ISerializable.

   1. Adicione o `[Serializable ()]` atributo à classe `demo`.

   Depois de concluir as alterações, o arquivo Class1.cs deverá ser semelhante ao seguinte:

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

1. Recompile o projeto.

## <a name="exclude-code-analysis-warnings"></a>Excluir avisos de análise de código

1. Para cada um dos avisos restantes, faça o seguinte:

    1. Selecione o aviso no **lista de erros**.

    1. No menu do clique com o botão direito do mouse (menu > de contexto), escolha suprimir**no arquivo de supressão**.

1. Recompile o projeto.

     O projeto é compilado sem avisos ou erros.

## <a name="see-also"></a>Consulte também

[Análise de código para código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md)