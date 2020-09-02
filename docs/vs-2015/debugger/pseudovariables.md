---
title: Pseudovariables | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9ce72d69cb64b0421771324803a785546fa884f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693761"
---
# <a name="pseudovariables"></a>Pseudovariáveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As pseudovariáveis são termos usados para exibir determinadas informações em uma janela de variável ou na caixa de diálogo do **QuickWatch**. Você pode inserir um pseudovariável da mesma maneira que incorporaria uma variável normal. As pseudovariáveis não são variáveis, no entanto, e não correspondem aos nomes de variáveis em seu programa.  
  
## <a name="example"></a>Exemplo  
 Suponha que você está escrevendo um aplicativo de código nativo e quer consultar o número de identificadores alocados em seu aplicativo. Na janela **Inspeção**, você pode inserir a seguinte pseudovariável na coluna **Nome** e então pressionar Enter para avaliá-la:  
  
```  
$handles  
```  
  
 em código nativo, você pode usar as pseudovariáveis mostradas na tabela:  
  
|Pseudovariável|Função|  
|--------------------|--------------|  
|`$err`|Exibe o último conjunto de valores de erro com a função SetLastError. O valor que é exibido representa o que seria retornado pela função GetLastError.<br /><br /> Use `$err,hr` para ver o formulário decodificado deste valor. Por exemplo, se o erro mais recente fosse 3, `$err,hr` exibiria `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Exibe o número de manipuladores alocados em seu aplicativo.|  
|`$vframe`|Exibe o endereço do quadro de pilha atual.|  
|`$tid`|Exibe a ID do thread para o thread atual.|  
|`$env`|Exibe o bloco de ambiente no visualizador de cadeia de caracteres.|  
|`$cmdline`|Exibe a cadeia de caracteres de linha de comando que iniciou o programa.|  
|`$pid`|Exibe a identificação do processo.|  
|`$` *registername*<br /><br /> ou<br /><br /> `@` *registername*|Exibe o conteúdo do registro *registername*.<br /><br /> Normalmente, você pode exibir conteúdo do registro simplesmente inserindo o nome do registro. A única vez que você precisa usar essa sintaxe é quando o nome do registro sobrecarrega um nome de variável. Se o nome do registro for igual ao nome da variável no escopo atual, o depurador interpretará o nome como um nome de variável. É nesse momento que `$`*registername* ou `@`*registername* é útil.|  
|`$clk`|Exibe a hora em ciclos de relógio.|  
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo. Por motivo de segurança, as informações de senha não são exibidas.|  
|`$exceptionstack`|Exibe o rastreamento de pilha da exceção atual de Windows Runtime. `$ exceptionstack` funciona somente em aplicativos da Store em execução no Windows 8.1 ou posterior. `$ exceptionstack` Não tem suporte para exceções do C++ e da sua|  
|`$ReturnValue`|Mostra o valor retornado de um método .NET Framework. Consulte [examinar valores de retorno de chamadas de método](https://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 No C# e no Visual Basic, você pode usar as pseudovariáveis mostradas na tabela:  
  
|Pseudovariável|Função|  
|--------------------|--------------|  
|`$exception`|Exibe informações sobre a última exceção. Se nenhuma exceção tiver ocorrido, a avaliação `$exception` exibirá uma mensagem de erro.<br /><br /> Somente no Visual C#, quando o Assistente de Exceção for desabilitado, `$exception` será automaticamente adicionado à janela **Locais** quando ocorrer uma exceção.|  
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo. Por motivo de segurança, as informações de senha não são exibidas.|  
  
 No Visual Basic, você pode usar as pseudovariáveis mostradas na seguinte tabela:  
  
|Pseudovariável|Função|  
|--------------------|--------------|  
|`$delete` ou `$$delete`|Exclui uma variável implícita criada na janela **Imediato**. A sintaxe é `$delete,` *variável* ou `$delete,` *variável*`.`|  
|`$objectids` ou `$listobjectids`|Exibe todas as IDs de objetos como filhos da expressão especificada. A sintaxe é `$objectid,` *expressão* ou `$listobjectids,` *expressão*`.`|  
|`$` *N* `#`|Exibe o objeto com a ID de objeto igual a *N*.|  
|`$dynamic`|Exibe o nó especial **Modo de Exibição Dinâmico** para um objeto que implementa o `IDynamicMetaObjectProvider`. Interface. A sintaxe é `$dynamic,` *objeto*. Esse recurso se aplica somente ao código que usa o .NET Framework versão 4. Consulte [modo de exibição dinâmico](https://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Consulte Também  
 [Janelas Watch e QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Janelas de Variáveis](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
