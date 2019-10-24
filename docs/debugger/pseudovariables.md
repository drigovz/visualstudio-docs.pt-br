---
title: Pseudovariables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e328e85f58e69ef1d579fd979f629c59b90caf3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730513"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudovariables no depurador do Visual Studio
As pseudovariáveis são termos usados para exibir determinadas informações em uma janela de variável ou na caixa de diálogo do **QuickWatch**. Você pode inserir um pseudovariável da mesma maneira que incorporaria uma variável normal. As pseudovariáveis não são variáveis, no entanto, e não correspondem aos nomes de variáveis em seu programa.

## <a name="example"></a>Exemplo
 Suponha que você está escrevendo um aplicativo de código nativo e quer consultar o número de identificadores alocados em seu aplicativo. Na janela **Inspeção**, você pode inserir a seguinte pseudovariável na coluna **Nome** e então pressionar Enter para avaliá-la:

`$handles`

 No código nativo, você pode usar o pseudovariables mostrado na tabela a seguir:

|Pseudovariável|Função|
|--------------------|--------------|
|`$err`|Exibe o último conjunto de valores de erro com a função SetLastError. O valor que é exibido representa o que seria retornado pela função GetLastError.<br /><br /> Use `$err,hr` para ver o formulário decodificado deste valor. Por exemplo, se o erro mais recente fosse 3, `$err,hr` exibiria `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|
|`$handles`|Exibe o número de manipuladores alocados em seu aplicativo.|
|`$vframe`|Exibe o endereço do quadro de pilha atual.|
|`$tid`|Exibe a ID do thread para o thread atual.|
|`$env`|Exibe o bloco de ambiente no visualizador de cadeia de caracteres.|
|`$cmdline`|Exibe a cadeia de caracteres de linha de comando que iniciou o programa.|
|`$pid`|Exibe a ID do processo.|
|`$` *registername*<br /><br /> ou<br /><br /> `@` *registername*|Exibe o conteúdo do registro *registername*.<br /><br /> Normalmente, você pode exibir conteúdo do registro simplesmente inserindo o nome do registro. A única vez que você precisa usar essa sintaxe é quando o nome do registro sobrecarrega um nome de variável. Se o nome do registro for igual ao nome da variável no escopo atual, o depurador interpretará o nome como um nome de variável. É nesse momento que `$`*registername* ou `@`*registername* é útil.|
|`$clk`|Exibe a hora em ciclos de relógio.|
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo. Por motivo de segurança, as informações de senha não são exibidas.|
|`$exceptionstack`|Exibe o rastreamento de pilha da exceção atual de Tempo de Execução do Windows. `$ exceptionstack` funciona somente em aplicativos UWP. Não há suporte para `$ exceptionstack` C++ para exceções Seh e|
|`$returnvalue`|Exibe o valor de retorno de um método .NET.|

 No C# , você pode usar o pseudovariables mostrado na tabela a seguir:

|Pseudovariável|Função|
|--------------------|--------------|
|`$exception`|Exibe informações sobre a última exceção. Se nenhuma exceção tiver ocorrido, a avaliação `$exception` exibirá uma mensagem de erro.<br /><br /> Quando o assistente de exceção é desabilitado, `$exception` é automaticamente adicionado à janela **locais** quando ocorre uma exceção.|
|`$user`|Exibe uma estrutura com informações de conta para a conta que executa o aplicativo. Por motivo de segurança, as informações de senha não são exibidas.|
|`$returnvalue`|Exibe o valor de retorno de um método .NET.|

 No Visual Basic, você pode usar as pseudovariáveis mostradas na seguinte tabela:

|Pseudovariável|Função|
|--------------------|--------------|
|`$exception`|Exibe informações sobre a última exceção. Se nenhuma exceção tiver ocorrido, a avaliação `$exception` exibirá uma mensagem de erro.|
|`$delete` ou `$$delete`|Exclui uma variável implícita criada na janela **Imediato**. A sintaxe é `$delete,` *variável* ou `$delete,` *variável* `.`|
|`$objectids` ou `$listobjectids`|Exibe todas as IDs de objetos como filhos da expressão especificada. A sintaxe *é `$objectid,` expressão `$listobjectids,` expressão `.`*|
|`$` *N* `#`|Exibe o objeto com a ID de objeto igual a *N*.|
|`$dynamic`|Exibe o nó especial **Modo de Exibição Dinâmico** para um objeto que implementa o `IDynamicMetaObjectProvider`. Interface. A sintaxe é `$dynamic,` *objeto*. Esse recurso se aplica somente ao código que usa .NET Framework versão 4 ou posterior.|

## <a name="see-also"></a>Consulte também
- [Janelas Inspeção e Inspeção Rápida](../debugger/watch-and-quickwatch-windows.md)
- [Janelas de Variáveis](../debugger/debugger-windows.md)
