---
title: 'Como: Ignorar erros em tarefas | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6d56c1b4e22250f56592e45d56c433c7ad78065
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024793"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Como: Ignorar erros em tarefas
Às vezes você deseja que um build seja tolerante a falhas em determinadas tarefas. Se essas tarefas não críticas falharem, você deseja que o build continue, pois ela ainda pode produzir a saída necessária. Por exemplo, se um projeto usa uma tarefa `SendMail` para enviar uma mensagem de email depois que cada componente é compilado, você pode considerar aceitável que o build prossiga até a conclusão, mesmo que os servidores de email não estejam disponíveis e as mensagens de status não possam ser enviadas. Ou, por exemplo, se arquivos intermediários são geralmente excluídos durante o build, você pode considerar aceitável que o build prossiga até a conclusão, mesmo que esses arquivos não possam ser excluídos.  
  
## <a name="use-the-continueonerror-attribute"></a>Usar o atributo ContinueOnError  
 O atributo `ContinueOnError` do elemento `Task` controla se um build é interrompida ou continua quando ocorre uma falha de tarefa. Esse atributo também controla se os erros são tratados como erros ou avisos quando o build continua.  
  
 O atributo `ContinueOnError` pode conter um dos seguintes valores:  
  
- **WarnAndContinue** ou **verdadeiro**. Quando uma tarefa falha, as tarefas subsequentes no elemento de [Destino](../msbuild/target-element-msbuild.md) e o build continuam em execução e todos os erros da tarefa são tratados como avisos.  
  
- **ErrorAndContinue**. Quando uma tarefa falha, as tarefas subsequentes no elemento de `Target` e o build continuam em execução e todos os erros da tarefa são tratados como erros.  
  
- **ErrorAndStop** ou **falso** (padrão). Quando uma tarefa falha, as tarefas restantes do elemento de `Target` e o build não são executadas e todo o elemento de `Target` e o build são considerados como em falha.  
  
  As versões do .NET Framework antes da 4.5 ofereciam suporte somente aos valores `true` e `false`.  
  
  O valor padrão de `ContinueOnError` é `ErrorAndStop`. Se você definir o atributo como `ErrorAndStop`, tornará o comportamento explícito para qualquer pessoa que lê o arquivo de projeto.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Para ignorar um erro em uma tarefa  
  
-   Use o atributo `ContinueOnError` da tarefa. Por exemplo:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra que o destino de `Build` ainda é executado e o build é considerada um sucesso, mesmo se a tarefa `Delete` falhar.  
  
```xml  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também
[MSBuild](../msbuild/msbuild.md)  
[Referência de tarefas](../msbuild/msbuild-task-reference.md)   
[Tarefas](../msbuild/msbuild-tasks.md)