---
title: Just My Code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302493"
---
# <a name="just-my-code"></a>Apenas Meu Código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os desenvolvedores que usam as linguagens do .NET Framework estão familiarizados com o depurador Apenas Meu Código que considera chamadas de sistema, de estrutura e outras chamadas não usuário e recolhe essas chamadas nas janelas de pilha de chamadas. Just My Code foi estendido para as línguas C++ e JavaScript. Este tópico descreve detalhes específicos do uso do Apenas Meu Código em projetos do .NET Framework, nativos do C++ e de JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Habilitar ou desabilitar Apenas Meu Código  
 Para ativar ou desativar Apenas Meu Código, escolha **Opções e Configurações** no menu **Depuração.** No nó**Geral** **de depuração,** / escolha ou **limpe Apenas Meu Código**.  
  
 ![Habilite apenas meu código na caixa de diálogo Opções](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> A **configuração Enable Just My Code** é uma configuração global que é aplicada a todos os projetos do Visual Studio em todos os idiomas.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>Filtragem de pilha de chamada de substituição  
 Em exibições de pilha de chamadas, como as janelas Pilha de chamadas e tarefas, `[External Code]`Just My Code colapsa o código de não-usuário em um quadro anotado. Para exibir os quadros colapsados, escolha **Mostrar código externo** no menu de contexto da exibição pilha de chamadas.  
  
> [!NOTE]
> A **configuração Mostrar código externo** é salva no profiler do usuário atual. Ela é aplicada a todos os projetos em todas as linguagens que são abertos pelo usuário.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework Just My Code  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>Código do usuário e não-usuário  
 Para distinguir o código do usuário do código não-usuário, just my code analisa arquivos símbolo (.pdb) e otimizações de programas. O depurador considera o código como sendo de não usuário quando o binário não é otimizado ou quando o arquivo .pdb não está disponível.  
  
 Três atributos também afetam o que o depurador considera como sendo Meu Código:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>diz ao depurador que o código a que é aplicado não é Meu Código.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta o código do depurador, mesmo que Apenas Meu Código esteja desativado.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>diz ao depurador para passar pelo código ao que é aplicado, em vez de entrar no código.  
  
  Todos os demais códigos são considerados código de usuário.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>Comportamento de pisada  
 Quando você **entra no** código de não-usuário (atalho do teclado: F11), o depurador passa sobre o código para a próxima declaração do usuário. Quando você **sai** (Teclado: Shift + F11), o depurador é executado para a próxima linha de código do usuário. Se nenhum código de usuário for encontrado, a execução continuará até que o aplicativo seja fechado, um ponto de interrupção seja atingido ou uma exceção ocorra.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>Comportamento de ponto de ruptura  
 Quando Just My Code estiver ativado, você pode escolher **Break All** (Teclado: Ctrl + Alt + Break) e interromper a execução em um local onde não há código de usuário para exibir. Quando isso acontece, a janela Sem Código Fonte será exibida. Se você escolher em um comando de etapa, o depurador leva você até a próxima linha do código do usuário.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>Comportamento de exceção  
 Se uma exceção sem tratamento ocorre no código de não usuário, o depurador é interrompido na linha do código de usuário na qual a exceção foi gerada.  
  
 Se as exceções de primeira opção estiverem habilitadas para a exceção, a linha do código de usuário será realçada em verde. A pilha de chamadas exibe um quadro anotado rotulado **[Código externo]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Apenas Meu Código do C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>Código do usuário e não-usuário  
 O Apenas Meu Código do C++ é diferente do Apenas Meu Código do .NET Framework e do JavaScript porque o comportamento de depuração é independente do comportamento da pilha de chamadas.  
  
 **Pilhas de chamadas**  
  
 Por padrão, o depurador considera estas funções como código de não usuário em janelas de pilha de chamadas:  
  
- Funções com informações de origem retiradas no respectivo arquivo de símbolos.  
  
- Funções nas quais os arquivos de símbolos indicam que não há nenhum arquivo de origem que corresponde ao quadro de pilhas.  
  
- Funções especificadas `*.natjmc` em `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` arquivos na pasta.  
  
  **Depuração**  
  
  Por padrão, apenas funções `*.natstepfilter` especificadas `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` em arquivos na pasta são consideradas código não-usuário.  
  
  Você pode criar `.natstepfilter` `.natjmc` o seu próprio e personalizar o `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`comportamento da janela de janela de passo e chamada no .  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>Comportamento de pisada  
 Quando você **entra (atalho** do teclado: F11) código não-usuário do código do usuário, o depurador passa sobre o código para a próxima linha de código de usuário. Quando você **sai** (Teclado: Shift + F11), o depurador é executado para a próxima linha de código do usuário. Se nenhum código de usuário for encontrado, a execução continuará até que o aplicativo seja fechado, um ponto de interrupção seja atingido ou uma exceção ocorra.  
  
 Se o depurador for interrompido em um código de não usuário (por exemplo, se um comando Interromper Tudo parar em um código de não usuário), a depuração continua no código de não usuário.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>Comportamento de exceção  
 Quando o depurador atinge uma exceção, ele parará na exceção independentemente de estar em código de usuário ou de não usuário. As opções **não manuseadas pelo usuário** na caixa de diálogo **Exceções** são ignoradas.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Personalize o comportamento de etapas  
 Você pode especificar funções a serem ultrapassadas `*.natstepfilter` listando-as como código não-usuário em arquivos.  
  
- Para especificar código não-usuário para todos os usuários da máquina Visual `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Studio, adicione o arquivo .natstepfilter à pasta.  
  
- Para especificar o código não-usuário para um usuário individual, `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` adicione o arquivo .natstepfilter à pasta.  
  
  Os arquivos .natstepfilter são arquivos XML com esta sintaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Função|Obrigatórios. Especifica uma ou mais funções como funções de não usuário.|  
|`Name`|Obrigatórios. Uma expressão regular formatada como ECMA-262 que especifica o nome completo da função a ser correspondida. Por exemplo: <br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> informa ao depurador que todos os métodos em `MyNS::MyClass` devem ser considerados como código de não usuário. A correspondência diferencia maiúsculas e minúsculas.|  
|`Module`|Opcional. Uma expressão regular formatada como ECMA-262 que especifica o caminho completo do módulo que contém a função. A correspondência não diferencia maiúsculas de minúsculas.|  
|`Action`|Obrigatórios. Um destes valores que diferenciam maiúsculas e minúsculas:<br /><br /> -   `NoStepInto`– diz ao depurador para passar por cima da função combinada.<br />-   `StepInto`– diz ao depurador para entrar nas funções `NoStepInto` combinadas, substituindo qualquer outra para as funções combinadas.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Personalizar o comportamento da pilha de chamadas  
 Você pode especificar módulos, arquivos de origem e funções para tratar como `*.natjmc` código não-usuário em pilhas de chamadas especificando-os em arquivos.  
  
- Para especificar código não-usuário para todos os usuários da máquina Visual `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Studio, adicione o arquivo .natjmc à pasta.  
  
- Para especificar o código não-usuário para um usuário individual, adicione o arquivo .natjmc à `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` pasta.  
  
  Os arquivos .natjmc são arquivos XML com esta sintaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Atributos do elemento de módulo**  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Obrigatórios. O caminho completo do módulo ou dos módulos. Você pode usar os `?` caracteres curinga `*` do Windows (zero ou um caractere) e (zero ou mais caracteres). Por exemplo,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> diz ao depurador para tratar `\3rdParty\UtilLibs` todos os módulos em qualquer unidade como código externo.|  
|`Company`|Opcional. O nome da empresa que publica o módulo inserido no arquivo executável. Você pode usar esse atributo para resolver a ambiguidade dos módulos.|  
  
 **Atributos do elemento de arquivo**  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Obrigatórios. O caminho completo do arquivo ou arquivos de origem a serem tratados como código externo. Você pode usar os caracteres curinga do Windows `?` e `*` quando especificar o caminho.|  
  
 **Atributos do elemento de função**  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Obrigatórios. O nome totalmente qualificado da função a ser tratada como código externo.|  
|`Module`|Opcional. O nome ou o caminho completo do módulo que contém a função. Você pode usar esse atributo para resolver a ambiguidade de funções com o mesmo nome.|  
|`ExceptionImplementation`|Quando configurado para `true`, a pilha de chamadas exibe a função que jogou a exceção em vez desta função.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Apenas Meu Código do JavaScript  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>Código do usuário e não-usuário  
 **Classificações de código**  
  
 O Apenas Meu Código do JavaScript controla a depuração e a exibição da pilha de chamadas categorizando o código em uma destas classificações:  
  
|||  
|-|-|  
|**MyCode**|Código do usuário que você possui e controla.|  
|**LibraryCode**|Código de não usuário de bibliotecas que você usa com frequência e do qual seu aplicativo depende para funcionar corretamente (por exemplo WinJS ou jQuery).|  
|**UnrelatedCode**|Código de não-usuário que poderia estar sendo executado em seu aplicativo, mas você não possui e seu aplicativo não depende diretamente dele para funcionar corretamente (por exemplo, um SDK de publicidade que exibe anúncios). Em projetos da Windows Store, todo código que é carregado no seu aplicativo a partir de um URI HTTP ou HTTPS também é considerado UnrelatedCode.|  
  
 O depurador do JavaScript classifica automaticamente estes tipos de código:  
  
- O script executado passando uma seqüência de `eval` string para a função fornecida pelo host é classificado como **MyCode**.  
  
- O script executado passando uma seqüência para o `Function` construtor é classificado como **LibraryCode**.  
  
- O script contido em uma referência de estrutura, como o WinJS ou o Azure SDK, é classificado como **LibraryCode**.  
  
- O script executado passando uma seqüência para as `setTimeout` `setImmediate` `setInterval` funções ou funções é classificado como **UnrelatedCode**.  
  
- O `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` especifica outro código de usuário e não-usuário para todos os projetos Visual Studio JavaScript.  
  
  Você pode alterar as classificações padrão e classificar arquivos e URLs específicos adicionando um arquivo .json nomeado `mycode.json` à pasta raiz de um projeto.  
  
  Todos os demais códigos são classificados como **MyCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>Comportamento de pisada  
  
- Se uma função não for código do usuário **(MyCode),** **Step Into** (atalho de teclado: F11) comporta-se como **Step Over** (Teclado: F10).  
  
- Se uma etapa começar no código não-usuário **(LibraryCode** ou **UnrelatedCode),** então a etapa se comporta temporariamente como se apenas meu código não estivesse habilitado. Assim que você percorrer de volta até o código de usuário, a depuração de Apenas Meu Código será habilitada novamente.  
  
- Quando uma etapa no código de usuário resultar na saída do contexto de execução atual (por exemplo, executar uma etapa na última linha de um manipulador de eventos), o depurador para na próxima linha de código de usuário executada. Por exemplo, se um retorno de chamada for executado no código **LibraryCode,** o depurador continuará até que a próxima linha de código do usuário seja executada.  
  
- **Step Out** (Teclado: Shift + F11) pára na próxima linha de código do usuário. Se nenhum código de usuário for encontrado, a execução continuará até que o aplicativo seja fechado, um ponto de interrupção seja atingido ou uma exceção ocorra.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>Comportamento de ponto de ruptura  
  
- Os pontos de interrupção definidos em qualquer código serão sempre atingidos independentemente da classificação desse código  
  
- Se `debugger` a palavra-chave for encontrada em:  
  
  - **Código de código de biblioteca,** o depurador sempre quebra.  

  - Código de código **não relacionado,** o depurador não pára.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>Comportamento de exceção  
 Se ocorrer uma exceção não tratada em:  
  
- **MyCode** ou **LibraryCode** code, o depurador sempre quebra.  
  
- **Código não relacionadoCódigo,** e **MyCode** ou **Código de LibraryCode** está na pilha de chamadas, o depurador é desfaz.  
  
  Se as exceções de primeira chance estiverem habilitadas para a exceção na caixa de diálogo Exceções e a exceção for lançada no **código LibraryCode** ou **UnrelatedCode:**  
  
- Se a exceção for tratada, o depurador não será interrompido.  
  
- Se a exceção não for tratada, o depurador será interrompido.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Personalizar apenas meu código  
 Para categorizar código de usuário e de não usuário para um único projeto do Visual Studio, adicione um arquivo .json denominado `mycode.json` à pasta raiz do projeto.  
  
 As classificações são executadas nesta ordem:  
  
1. Classificações padrão  
  
2. Classificações no `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` arquivo  
  
3. Classificações no arquivo `mycode. json` do projeto atual.  
  
   Cada etapa de classificação substitui as etapas anteriores. Um arquivo .json não precisa listar todos os pares de valores-chave, e os valores **MyCode,** **Bibliotecas**e **Não Relacionados** podem ser matrizes vazias.  
  
   Os arquivos .json MyCode usam esta sintaxe:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function e ScriptBlock**  
  
 Os pares de valores-chave **Eval,** **Function**e **ScriptBlock** determinam como o código gerado dinamicamente é classificado.  
  
|||  
|-|-|  
|**Eval**|Script que é executado passando uma cadeia de caracteres à função `eval` fornecida pelo host. Por padrão, o script Eval é classificado como **MyCode**.|  
|**Função**|Script que é executado passando uma cadeia de caracteres para o construtor `Function`. Por padrão, o script Function é classificado como **LibraryCode**.|  
|**ScriptBlock**|Script que é executado passando uma cadeia de caracteres para a função `setTimeout`, `setImmediate` ou `setInterval`. Por padrão, o script ScriptBlock é classificado como **UnrelatedCode**.|  
  
 Você pode alterar o valor para um destas palavras-chave:  
  
- `MyCode`classifica o script como **MyCode**.  
  
- `Library`classifica o script como **LibraryCode**.  
  
- `Unrelated`classifica o script como **Não RelacionadoCódigo**.  
  
  **MyCode, Libraries e Unrelated**  
  
  Os pares de valores-chave **MyCode,** **Libraryes** **e Não relacionados** especificam as urls ou arquivos que você deseja incluir em uma classificação:  
  
|||  
|-|-|  
|**MyCode**|Uma matriz de urls ou arquivos classificados como **MyCode**.|  
|**Bibliotecas**|Uma matriz de urls ou arquivos classificados como **LibraryCode**.|  
|**Unrelated**|Uma matriz de urls ou arquivos classificados como **UnrelatedCode**.|  
  
 A seqüência de url `*` ou arquivo pode conter um ou mais caracteres, que correspondem a zero ou mais caracteres. `*`é o equivalente à `.*`expressão regular.
