---
title: Gerenciar exceções com o depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302150"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gerenciar exceções com o depurador no Visual Studio

Uma exceção é uma indicação de um estado de erro que ocorre enquanto um programa está sendo executado. Você pode dizer ao depurador quais exceções ou conjuntos de exceções para quebrar, e em que ponto você quer que o depurador quebre (ou seja, pausa no depurador). Quando o depurador quebra, mostra onde a exceção foi jogada. Você também pode adicionar ou excluir exceções. Com uma solução aberta no Visual Studio, use **Debug > Configurações** de exceção do Windows > para abrir a janela **Configurações de exceção.**

Forneça manipuladores que respondam às exceções mais importantes. Se você precisar saber como adicionar manipuladores para exceções, consulte [Corrigir bugs escrevendo um código C# melhor](../debugger/write-better-code-with-visual-studio.md). Além disso, aprenda a configurar o depurador para sempre quebrar a execução para algumas exceções.

Quando ocorre uma exceção, o depurador grava uma mensagem de exceção na janela **Saída.** Pode interromper a execução nos seguintes casos quando:

- Uma exceção é lançada que não é tratada.
- O depurador está configurado para interromper a execução antes que qualquer manipulador seja invocado.
- Você definiu [Just My Code](../debugger/just-my-code.md), e o depurador está configurado para quebrar qualquer exceção que não seja tratada no código do usuário.

> [!NOTE]
> ASP.NET tem um manipulador de exceção de alto nível que mostra páginas de erro em um navegador. Não quebra a execução a menos que **meu código** esteja ligado. Por exemplo, [consulte Diga ao depurador para continuar em exceções não manipuladas pelo usuário](#BKMK_UserUnhandled) abaixo.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Em um aplicativo Visual Basic, o depurador gerencia todos os erros como exceções, mesmo se você usar manipuladores de erros no estilo Deerro.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Diga ao depurador para quebrar quando uma exceção for lançada

O depurador pode interromper a execução no ponto em que uma exceção é lançada, para que você possa examinar a exceção antes que um manipulador seja invocado.

Na janela **Configurações de exceção** **(Debug > Configurações de exceção do Windows >),** expanda o nó para uma categoria de exceções, como **exceções de tempo de execução de idioma sumido.** Em seguida, selecione a caixa de seleção para uma exceção específica dentro dessa categoria, como **System.AccessViolationException**. Você também pode selecionar uma categoria inteira de exceções.

![Verificada violação de acessosViolação de violação](../debugger/media/exceptionsettingscheckaccess.png "ExceçõesConfiguraçõesVerificaçãodeacesso")

> [!TIP]
> Você pode encontrar exceções específicas usando a janela **pesquisar** na barra de **ferramentas Configurações** de exceção ou usar a pesquisa para filtrar espaços de nome específicos (como **System.IO**).

Se você selecionar uma exceção na janela **Configurações de exceção,** a execução do depurador quebrará onde quer que a exceção seja lançada, não importa se ela for tratada. Agora a exceção é chamada de exceção de primeira chance. Por exemplo, aqui estão alguns cenários:

- No aplicativo de console C# a seguir, o `try/catch` método Principal lança uma **AccessViolationException** dentro de um bloco.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  Se você tiver **o AccessViolationException** verificado nas **Configurações de Exceção,** a `throw` execução será rompida na linha quando você executar este código no depurador. Você pode continuar a execução. O console deve exibir ambas as linhas:

  ```cmd
  caught exception
  goodbye
  ```

  mas não exibe a `here` linha.

- Um aplicativo de console C# faz referência a uma biblioteca de classes com uma classe que tem dois métodos. Um método lança uma exceção e lida com ela, enquanto um segundo método lança a mesma exceção, mas não lida com isso.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Aqui está o método Principal() da aplicação do console:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Se você tiver **o AccessViolationException** verificado nas **Configurações de exceção,** a `throw` execução será rompida na linha tanto no **ThrowHandledException()** quanto **no ThrowUnhandledException()** quando você executar esse código no depurador.

Para restaurar as configurações de exceção aos padrões, escolha Restaurar a lista no botão **configurações padrão:**

![Restaurar padrões em Configurações de exceção](../debugger/media/restoredefaultexceptions.png "RestaurarExceções de padrão")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Diga ao depurador para continuar em exceções não manipuladas pelo usuário

Se você estiver depurando o código .NET ou JavaScript com [Just My Code,](../debugger/just-my-code.md)você pode dizer ao depurador para evitar a quebra de exceções que não são tratadas no código do usuário, mas são tratadas em outros lugares.

1. Na janela **Configurações de exceção,** abra o menu de atalho clicando com o botão direito do mouse em um rótulo de coluna e, em seguida, selecione **Mostrar colunas > Ações adicionais**. (Se você desligou **Just My Code,** você não verá este comando.) Uma terceira coluna chamada **Ações Adicionais** aparece.

   ![Coluna Ações Adicionais](../debugger/media/additionalactionscolumn.png "AdicionaisAçõesColuna")

   Para uma exceção que mostra **Continuar quando não manipulado no código do usuário** nesta coluna, o depurador continua se essa exceção não for tratada no código do usuário, mas for tratada externamente.

2. Para alterar essa configuração para uma exceção específica, selecione a exceção, clique com o botão direito do mouse para mostrar o menu de atalho e selecione **Continuar quando não for manipulado em Código de Usuário**. Você também pode alterar a configuração para uma categoria inteira de exceções, como as exceções de tempo de execução do idioma comum).

   ![**Continuar quando não for manuseado na configuração de código do usuário**](../debugger/media/continuewhenunhandledinusercodesetting.png "Continuarquandonão lidoucomInUserCodeSetting")

Por exemplo, ASP.NET aplicativos web lidam com exceções convertendo-as em um código de status HTTP 500 ([Manipulação de exceções em ASP.NET API da Web),](/aspnet/web-api/overview/error-handling/exception-handling)o que pode não ajudá-lo a determinar a fonte da exceção. No exemplo abaixo, o código do `String.Format()` usuário <xref:System.FormatException>faz uma chamada para que lança um . A execução quebra da seguinte forma:

![Quebras na exceção&#45;do usuário](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Adicionar e excluir exceções

Você pode adicionar e excluir exceções. Para excluir um tipo de exceção de uma categoria, selecione a exceção e escolha **Excluir a exceção selecionada no** botão lista (o sinal de menos) na barra de ferramentas **Configurações de exceção.** Ou você pode clicar com o botão direito do mouse na exceção e selecionar **Excluir** no menu de atalho. Excluir uma exceção tem o mesmo efeito de ter a exceção desmarcada, que é que o depurador não quebra quando é jogado.

Para adicionar uma exceção:

1. Na janela **Configurações de exceção,** selecione uma das categorias de exceção (por exemplo, **Tempo de execução do idioma comum**).

2. Escolha o **Adicionar uma exceção ao** botão de categoria selecionado (o sinal de mais).

   ![**Adicione uma exceção ao botão de categoria selecionada**](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddanExceptionToTheSelectedCategorybutton")

3. Digite o nome da exceção (por exemplo, **System.UriTemplateMatchException**).

   ![Digite o nome de exceção](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   A exceção é adicionada à lista (em ordem alfabética) e verificada automaticamente.

Para adicionar uma exceção às exceções de acesso à memória da GPU, as categorias JavaScript Runtime Exceptions ou Win32 Exceptions, inclua o código de erro e a descrição.

> [!TIP]
> Verifique a ortografia. A janela **Configurações de exceção** não verifica a existência de uma exceção adicional. Portanto, se você digitar **Sytem.UriTemplateMatchException,** você terá uma entrada para essa exceção (e não para **System.UriTemplateMatchException**).

As configurações de exceção são persistidas no arquivo .suo da solução, de modo que se aplicam a uma solução específica. Você não pode reutilizar configurações específicas de exceção entre as soluções. Agora, apenas exceções adicionais são persistidas; exceções excluídas não são. Você pode adicionar uma exceção, fechar e reabrir a solução, e a exceção ainda estará lá. Mas se você excluir uma exceção e fechar/reabrir a solução, a exceção reaparecerá.

A janela **Configurações de exceção** suporta tipos genéricos de exceção em C#, mas não no Visual Basic. Para quebrar exceções `MyNamespace.GenericException<T>`como , você deve adicionar a exceção como **MyNamespace.GenericException'1**. Isto é, se você criou uma exceção como este código:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Você pode adicionar a exceção às **Configurações de exceção** usando o procedimento anterior:

![adicionando exceção genérica](../debugger/media/addgenericexception.png "AdicionarGenericException")

## <a name="add-conditions-to-an-exception"></a>Adicionar condições a uma exceção

Use a janela **Configurações de exceção** para definir condições em exceções. As condições atualmente suportadas incluem o nome do módulo para incluir ou excluir para a exceção. Ao definir nomes de módulos como condições, você pode optar por quebrar para a exceção apenas em determinados módulos de código. Você também pode optar por evitar quebrar em módulos específicos.

> [!NOTE]
> A adição de condições a [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]uma exceção é suportada a partir de .

Para adicionar exceções condicionais:

1. Escolha o botão **Editar condições** na janela Configurações de exceção ou clique com o botão direito do mouse na exceção e escolha **Editar condições**.

   ![Condições para uma exceção](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Para adicionar condições extras necessárias à exceção, **selecione Adicionar Condição** para cada nova condição. Linhas de condição adicionais aparecem.

   ![Condições extras para uma exceção](../debugger/media/extraconditionsforanexception.png "ExtraCondiçõesParaUma Exceção")

3. Para cada linha de condição, digite o nome do módulo e altere a lista do operador de comparação para **Equals** ou **Not Equals**. Você pode especificar**\\**curingas () no nome para especificar mais de um módulo.

4. Se você precisar excluir uma condição, escolha o **X** no final da linha de condição.

## <a name="see-also"></a>Confira também

- [Continuar a execução depois de uma exceção](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Como examinar um código de sistema após uma exceção](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Como usar verificações de tempo de execução nativas](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Use verificações de tempo de execução sem a biblioteca c de tempo de execução](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Primeiro olhe para o depurador](../debugger/debugger-feature-tour.md)
