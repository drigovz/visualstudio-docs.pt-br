---
title: Gerenciando exceções com o depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5303a8003d84af5e2a059d9f509e560204afa528
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301096"
---
# <a name="managing-exceptions-with-the-debugger"></a>Gerenciando exceções com o depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma exceção é uma indicação de um estado de erro que ocorre enquanto um programa está sendo executado. Você pode e deve fornecer manipuladores que respondem às exceções mais importantes, mas é importante saber como configurar o depurador para interromper as exceções que você deseja ver.  
  
 Quando ocorre uma exceção, o depurador grava uma mensagem de exceção na janela de saída. Ele pode interromper a execução nos seguintes casos:  
  
- Quando uma exceção é lançada e não é manipulada.  
  
- Quando o depurador é definido para interromper a execução imediatamente quando uma exceção é lançada, antes de qualquer manipulador ser invocado.  
  
- Se você tiver definido [apenas meu código](../debugger/just-my-code.md)e o depurador estiver definido para interromper qualquer exceção que não seja tratada no código do usuário.  
  
> [!NOTE]
> ASP.NET tem um manipulador de exceção de nível superior que mostra páginas de erro em um navegador. Ele não interrompe a execução, a menos que **apenas meu código** esteja ativado. Para obter um exemplo, consulte [definindo o depurador para continuar nas exceções sem tratamento do usuário](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) abaixo.  
  
> [!NOTE]
> Em um aplicativo Visual Basic, o depurador gerencia todos os erros como exceções, mesmo que você use os manipuladores de erro de estilo de erro.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Gerenciando exceções com a janela configurações de exceção  
 Você pode usar a janela **configurações de exceção** para especificar quais exceções (ou conjuntos de exceções) farão com que o depurador seja interrompido e, nesse ponto, você deseja interromper. Você pode adicionar ou excluir exceções ou especificar exceções para interromper. Abra esta janela quando uma solução estiver aberta clicando em **depurar/Windows/configurações de exceção**.  
  
 Você pode encontrar exceções específicas usando a janela **Pesquisar** na barra de ferramentas **configurações de exceção** ou usar Pesquisar para filtrar namespaces específicos (por exemplo, **System.Io**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Definindo o depurador a ser interrompido quando uma exceção é gerada  
 O depurador pode interromper a execução no ponto em que uma exceção é lançada, dando a você a oportunidade de examinar a exceção antes que um manipulador seja invocado.  
  
 Na janela **configurações de exceção** , expanda o nó de uma categoria de exceções (por exemplo, **exceções do Common Language Runtime**, significando exceções .net) e marque a caixa de seleção para uma exceção específica dentro dessa categoria (por exemplo, **System. AccessViolationException**). Você também pode selecionar uma categoria inteira de exceções.  
  
 ![AccessViolationException verificada](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Se você marcar uma determinada exceção, a execução do depurador será interrompida sempre que a exceção for lançada, independentemente de ser manipulada ou não manipulada. Neste ponto, a exceção é chamada de uma exceção de primeira chance. Por exemplo, aqui estão alguns cenários:  
  
1. No aplicativo de C# console a seguir, o método Main gera um **AccessViolationException** dentro de um bloco de `try/catch`:  
  
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
  
    Se você tiver o **AccessViolationException** verificado nas **configurações de exceção**, quando você executar esse código na execução do depurador será interrompido na linha de `throw`. Em seguida, você pode continuar a execução. O console deve exibir as duas linhas:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    Mas não exibe a linha de `here`.  
  
2. Um C# aplicativo de console faz referência a uma biblioteca de classes com uma classe que tem dois métodos, um método que gera uma exceção e a trata e um segundo método que gera a mesma exceção e não a trata:  
  
   ```vb  
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
  
    Aqui está o método Main () do aplicativo de console:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       Class1 class1 = new Class1();  
       class1.ThrowHandledException();  
       class1.ThrowUnhandledException();  
   }  
   ```  
  
    Se você tiver o **AccessViolationException** verificado nas **configurações de exceção**, quando você executar esse código na execução do depurador será interrompido na linha de `throw` em **ThrowHandledException ()** e **ThrowUnhandledException ()** .  
  
   Se desejar restaurar as configurações de exceção para os padrões, você pode clicar no botão **restaurar** na barra de ferramentas:  
  
   ![Restaurar padrões nas configurações de exceção](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="BKMK_UserUnhandled"></a>Definindo o depurador para continuar em exceções não tratadas pelo usuário  
 Se estiver depurando código .NET ou JavaScript com [apenas meu código](../debugger/just-my-code.md), você poderá dizer ao depurador para não interromper exceções que não são tratadas no código do usuário, mas que são tratadas em outro lugar.  
  
1. Na janela **configurações de exceção** , abra o menu de contexto clicando com o botão direito do mouse em janela e selecionando **Mostrar colunas**. (Se você tiver desativado **apenas meu código**, não verá esse comando.)  
  
2. Você deverá ver uma segunda coluna denominada **ações adicionais**. Essa coluna exibe **continuar quando não tratado pelo código do usuário** em exceções específicas, o que significa que o depurador não interromperá se essa exceção não for tratada no código do usuário, mas for manipulada no código externo.  
  
3. Você pode alterar essa configuração para uma exceção específica (selecione a exceção, clique com o botão direito do mouse e selecione/desmarque a opção **continuar quando não for tratado no código do usuário**) ou para uma categoria inteira de exceções (por exemplo, todas as exceções de Common Language Runtime).  
  
   Por exemplo, aplicativos Web ASP.NET lidam com exceções convertendo-as em um código de status HTTP 500 ([tratamento de exceção na API ASP.net](https://docs.microsoft.com/aspnet/web-api/overview/error-handling/exception-handling)), o que pode não ajudá-lo a determinar a origem da exceção. No exemplo a seguir, o código do usuário faz uma chamada para `String.Format()` que gera um <xref:System.FormatException>. A execução é interrompida da seguinte maneira:  
  
   ![quebras na&#45;exceção de unhanlded do usuário](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Adicionando e excluindo exceções  
 Você pode adicionar e excluir exceções. Você pode excluir qualquer tipo de exceção de qualquer categoria, selecionando a exceção e clicando no botão **excluir** (o sinal de subtração) na barra de ferramentas **configurações de exceção** ou clicando com o botão direito do mouse na exceção e selecionando **excluir** no menu de contexto. Excluir uma exceção tem o mesmo efeito que ter a exceção desmarcada, o que é que o depurador não será interrompido quando for gerado.  
  
 Para adicionar uma exceção: na janela **configurações de exceção** , selecione uma das categorias de exceção (por exemplo, **Common Language Runtime**) e clique no botão **Adicionar** . Digite o nome da exceção (por exemplo, **System.UriTemplateMatchException**). A exceção é adicionada à lista (em ordem alfabética) e é verificada automaticamente.  
  
 Se desejar adicionar uma exceção às exceções de acesso à memória da GPU, às exceções de tempo de execução do JavaScript ou às categorias de exceções Win32, você precisará incluir o código de erro, bem como a descrição.  
  
> [!TIP]
> Verifique a ortografia. A janela de **configurações de exceção** não verifica a existência de uma exceção adicionada. Portanto, se você digitar System **. UriTemplateMatchException**, receberá uma entrada para essa exceção (e não para o **sistema. UriTemplateMatchException**).  
  
 As configurações de exceção são mantidas no arquivo. suo da solução, portanto, elas se aplicam a uma solução específica. Não é possível reutilizar configurações de exceção específicas em soluções. Neste ponto, somente exceções adicionadas são persistidas; as exceções excluídas não são. Em outras palavras, você pode adicionar uma exceção, fechar e reabrir a solução, e a exceção ainda estará lá. Mas se você excluir uma exceção e fechar/reabrir a solução, a exceção será exibida novamente.  
  
 A janela de **configurações de exceção** dá suporte a C# tipos de exceção genérica no, mas não em Visual Basic. Para interromper exceções como `MyNamespace.GenericException<T>`, você deve adicionar a exceção como **MyNamespace. genericException ' 1**. Ou seja, se você tiver criado uma exceção como esta:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Você pode adicionar a exceção às **configurações de exceção** como esta:  
  
 ![adicionando exceção genérica](../debugger/media/addgenericexception.png "Addgenéricaexception")  
  
## <a name="see-also"></a>Consulte também  
 [Continuando a execução após uma exceção](../debugger/continuing-execution-after-an-exception.md)   
 [Como examinar o código do sistema após uma exceção](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Como: usar verificações de tempo de execução nativas](../debugger/how-to-use-native-run-time-checks.md)   
 [Usando verificações de tempo de execução sem a biblioteca de tempo de execução C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
   do [Assistente de exceção](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)  
 [Noções básicas do depurador](../debugger/debugger-basics.md)
