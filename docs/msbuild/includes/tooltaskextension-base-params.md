---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 6fd0fc6fd4f2e54c0d15f649139b649797f8336f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89042943"
---
### <a name="tooltaskextension-parameters"></a>Parâmetros de ToolTaskExtension

Essa tarefa herda da <xref:Microsoft.Build.Tasks.ToolTaskExtension> classe, que herda da <xref:Microsoft.Build.Utilities.ToolTask> classe, que em si herda da <xref:Microsoft.Build.Utilities.Task> classe. Esta cadeia de herança adiciona vários parâmetros nas tarefas que derivam deles.

A tabela a seguir descreve os parâmetros das classes base:

| Parâmetro | Descrição |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Parâmetro `bool` opcional.<br /><br /> Quando definido como `true`, essa tarefa passa **/Q** para a linha de comando de *cmd.exe*, de modo que a linha de comando não é copiada para stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Parâmetro de matriz `String` opcional.<br /><br /> Matriz de definições de variáveis de ambiente, separadas por ponto e vírgula. Cada definição deve especificar um nome de variável de ambiente e um valor separados por um sinal de igual. Essas variáveis são passadas para o executável gerado além, ou seletivamente substituindo, o bloco de ambiente regular. Por exemplo, `Variable1=Value1;Variable2=Value2`. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Parâmetro de saída opcional somente leitura `Int32`.<br /><br /> Especifica o código de saída fornecido pelo comando executado. Se a tarefa registra erros, mas o processo tem um código de saída de 0 (êxito), isso é definido como -1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Opção parâmetro `bool`.<br /><br /> Se `true`, todas as mensagens recebidas no fluxo de erro padrão são registradas como erros. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parâmetro `bool` opcional.<br /><br /> Se `true`, todas as mensagens recebidas no fluxo de erro padrão são registradas como erros. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Parâmetro `String` opcional.<br /><br /> Importância para fazer o texto de log do fluxo de saída do padrão. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Parâmetro `String` opcional.<br /><br /> Importância para fazer o texto de log do fluxo de saída do padrão. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Parâmetro `Int32` opcional.<br /><br /> Especifica a quantidade de tempo em milissegundos após o qual o executável da tarefa é encerrado. O valor padrão é `Int.MaxValue`, indicando que não há período de tempo limite. O tempo limite está em milissegundos. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Parâmetro `string` opcional.<br /><br /> Projetos podem implementar para substituir um ToolName. Tarefas podem substituir isso para preservar o ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Parâmetro `string` opcional.<br /><br /> Especifica o local de onde a tarefa carrega o arquivo executável subjacente. Se esse parâmetro não for especificado, a tarefa usará o caminho de instalação do SDK que corresponde à versão do Framework que está executando o MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Parâmetro `bool` opcional.<br /><br /> Quando definido como `true`, essa tarefa cria um arquivo em lotes para a linha de comando e o executa usando o processador de comando em vez de executar o comando diretamente. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Parâmetro `bool` opcional.<br /><br /> Quando definido como `true`, essa tarefa gera o nó quando a tarefa está em execução. |
