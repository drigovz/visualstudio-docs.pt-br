---
title: 'Walkthrough: analisando código gerenciado para defeitos de código | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609327"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Instruções passo a passo: analisando código gerenciado em busca de defeitos de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Neste tutorial, você analisa um projeto gerenciado para defeitos de código usando a ferramenta de análise de código.

 Este passo a passo irá orientá-lo pelo processo de uso da análise de código para analisar seus assemblies de código gerenciado .NET para conformidade com as diretrizes de design do Microsoft .NET Framework.

 Neste passo a passo, você vai:

- Analise e corrija avisos de defeito de código.

## <a name="prerequisites"></a>Pré-requisitos

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].

## <a name="create-a-class-library"></a>Criar uma biblioteca de classes

#### <a name="to-create-a-class-library"></a>Para criar uma biblioteca de classes

1. No menu **arquivo** do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , clique em **novo** e em **projeto**.

2. Na caixa de diálogo **novo projeto** , em **tipos de projeto**, clique em **Visual C#**.

3. Em **Modelos**, selecione **Biblioteca de Classes**.

4. Na caixa de texto **nome** , digite **CodeAnalysisManagedDemo** e clique em **OK**.

5. Depois que o projeto for criado, abra o arquivo Class1.cs.

6. Substitua o texto existente em Class1.cs pelo seguinte código:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Salve o arquivo Class1.cs.

## <a name="analyze-the-project"></a>Analisar o projeto

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analisar um projeto gerenciado para defeitos de código

1. Selecione o projeto CodeAnalysisManagedDemo em **Gerenciador de soluções**.

2. No menu **Projeto** , clique em **Propriedades**.

     A página de propriedades CodeAnalysisManagedDemo é exibida.

3. Clique em **CodeAnalysis**.

4. Verifique se a opção  **Habilitar análise de código na compilação (define CODE_ANALYSIS constante**) está marcada.

5. Na lista suspensa **executar esta regra definida** , selecione **todas as regras da Microsoft**.

6. No menu **arquivo** , clique em **salvar itens selecionados**e feche as páginas de propriedades do ManagedDemo.

7. No menu **Compilar** , clique em **criar ManagedDemo**.

     Os avisos de compilação do projeto CodeAnalysisManagedDemo são relatados nas janelas de **análise de código** e **saída** .

     Se a janela **análise de código** não aparecer, no menu **analisar** , escolha **Windows** e, em seguida, **escolha análise de código**.

## <a name="correct-the-code-analysis-issues"></a>Corrigir os problemas de análise de código

#### <a name="to-correct-code-analysis-rule-violations"></a>Para corrigir violações de regra de análise de código

1. No menu **Exibir** , clique em **Lista de Erros**.

     Dependendo do perfil de desenvolvedor que você escolheu, talvez seja necessário apontar para **outras janelas** no menu **Exibir** e clicar em **lista de erros**.

2. Em **Gerenciador de soluções**, clique em **Mostrar todos os arquivos**.

3. Em seguida, expanda o nó Propriedades e, em seguida, abra o arquivo AssemblyInfo.cs.

4. Use o seguinte para corrigir os avisos:

- [CA1014: Mark assemblies com CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: ' demo ' deve ser marcado com o CLSCompliantAttribute e seu valor deve ser true.

  - Adicione o código `using``System;` ao arquivo AssemblyInfo.cs.

       Em seguida, adicione o código `[assembly: CLSCompliant(true)]` ao final do arquivo AssemblyInfo.cs.

       Recompile o projeto.

- [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Adicione o seguinte construtor a esta classe: demonstração pública (cadeia de caracteres)

  - Adicione o construtor `public demo (String s) : base(s) { }` à classe `demo` .

- [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Adicione o seguinte construtor a esta classe: demonstração pública (cadeia de caracteres, exceção)

  - Adicione o construtor `public demo (String s, Exception e) : base(s, e) { }` à classe `demo` .

- [CA1032: Implementar construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Adicione o seguinte construtor a esta classe: demonstração protegida (SerializationInfo, StreamingContext)

  - Adicione o código `using System.Runtime.Serialization;` ao início do arquivo Class1.cs.

       Em seguida, adicione o Construtor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Recompile o projeto.

- [CA1032: implemente construtores de exceção padrão](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Adicione o seguinte construtor a esta classe: demonstração pública ()

  - Adicione o construtor `public demo () : base() { }` à classe `demo` **.**

       Recompile o projeto.

- [CA1709: os identificadores devem estar](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)em algum certo: Microsoft. Naming: corrija a capitalização do nome de namespace ' TestCode ' alterando-o para ' TestCode '.

  - Altere a capitalização do namespace `testCode` para `TestCode` .

- [CA1709: os identificadores devem estar](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)em algum certo: Microsoft. Naming: corrija a capitalização do nome de tipo ' demo ' alterando-o para ' demo '.

  - Altere o nome do membro para `Demo` .

- [CA1709: os identificadores devem estar](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)em algum certo: Microsoft. Naming: corrija a capitalização do nome de membro ' item ' alterando-o para ' item '.

  - Altere o nome do membro para `Item` .

- [CA1710: os identificadores devem ter o sufixo correto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: Renomear ' TestCode. demo ' para terminar em ' Exception '.

  - Altere o nome da classe e seus construtores para `DemoException` .

- [CA2210: assemblies devem ter nomes fortes válidos](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): assinar ' ManagedDemo ' com uma chave de nome forte.

  - No menu **projeto** , clique em **Propriedades de ManagedDemo**.

       As propriedades do projeto são exibidas.

       Clique em **assinatura**.

       Marque a caixa de seleção **assinar o assembly** .

       Na lista **escolher um arquivo de chave de nome de cadeia de caracteres** , selecione **\<New…>** .

       A caixa de diálogo **Criar Chave de Nome Forte** é aberta.

       No **nome do arquivo de chave**, digite TestKey.

       Insira uma senha e clique em **OK**.

       No menu **arquivo** , clique em **salvar itens selecionados**e feche as páginas de propriedades.

       Recompile o projeto.

- [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: adicionar um atributo [Serializable] ao tipo ' demo ', pois esse tipo implementa ISerializable.

  - Adicione o `[Serializable ()]` atributo à classe `demo` .

       Recompile o projeto.

  Depois de concluir as alterações, o arquivo Class1.cs deverá ser semelhante ao seguinte:

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Excluir avisos de análise de código

#### <a name="to-exclude-code-defect-warnings"></a>Para excluir avisos de defeito de código

1. Para cada um dos avisos restantes, faça o seguinte:

   1. Na janela análise de código, selecione o aviso.

   2. Escolha **ações**, escolha **suprimir mensagem**e, em seguida, escolha **no arquivo de supressão do projeto**.

      Para obter mais informações, consulte [como: suprimir avisos usando o item de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Recompile o projeto.

    O projeto é compilado sem avisos ou erros.
