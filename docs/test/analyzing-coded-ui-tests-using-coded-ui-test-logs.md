---
title: Analisando testes de interface de usuário codificada usando logs de teste de interface de usuário codificada
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 76aac39d50dc724916bca3d863c71bacf53407d9
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824492"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analisando testes de IU codificados usando logs de teste de IU codificado

Os logs de teste de IU codificado filtram e registram informações importantes sobre as execuções de teste de IU codificado. Os logs são apresentados em um formato que permite depurar os problemas rapidamente.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Etapa 1: Habilite o registro em logs

De acordo com seu cenário, use um destes métodos para habilitar o log:

- Se não houver um arquivo *App.config* presente em seu projeto de teste:

   1. Determine qual processo *QTAgent\*.exe* é iniciado quando você executa o teste. Uma maneira de fazer isso é observar a guia **Detalhes** no **Gerenciador de Tarefas** do Windows.
   
   2. Abra o arquivo *.config* correspondente da pasta *%ProgramFiles(x86)%\versão do Microsoft Visual Studio\\\<>\\\<edição>\Common7\IDE*. Por exemplo, se o processo que é executado é *QTAgent_40.exe*, abra *QTAgent_40.exe.config*.

   2. Modifique o valor de **EqtTraceLevel** para o nível de log desejado.
   
      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Salve o arquivo.

- Se houver um arquivo *App.config* presente em seu projeto de teste:

  - Abra o arquivo *App.config* no projeto e adicione o seguinte código sob o nó de configuração:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Habilitar registro em log do próprio código de teste:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Etapa 2: Execute o teste de IU codificado e veja o log

Ao executar um teste de IU codificado com as modificações no arquivo *QTAgent\*.exe.config* em vigor, você verá um link de saída nos resultados do **Gerenciador de Testes**. Os arquivos de log são gerados não apenas quando o teste falha, mas também quando o nível de rastreamento está definido como **detalhado** e os testes são bem-sucedidos.

1. No menu **Teste**, escolha a opção **Windows** e selecione **Gerenciador de Testes**.

2. No menu **Compilar**, escolha **Compilar Solução**.

3. No **Gerenciador de Testes**, selecione o teste de IU codificado que você deseja executar, abra seu menu de atalho e escolha em **Executar Testes Selecionados**.

     Os testes automatizados são executados e indicam se passaram ou falharam.

    > [!TIP]
    > Para exibir o **Gerenciador de Testes**, escolha **Teste** > **Windows** e escolha **Gerenciador de Testes**.

4. Clique no link **Saída** nos resultados do **Gerenciador de Testes**.

     ![Link de saída no Gerenciador de Testes](../test/media/cuit_htmlactionlog1.png)

     Essa ação exibe a saída do teste, que inclui um link ao log de ações.

     ![Resultados e links de saída do teste de IU codificado](../test/media/cuit_htmlactionlog2.png)

5. Escolha o link *UITestActionLog.html*.

     O log é exibido em seu navegador da Web.

     ![Arquivo de log do teste de IU codificado](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Consulte também

- [Usar a automação de interface do usuário para testar seu código](../test/use-ui-automation-to-test-your-code.md)
- [Como: Como executar testes no Microsoft Visual Studio](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
