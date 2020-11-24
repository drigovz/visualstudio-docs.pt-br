---
title: Criando e executando testes de unidade para aplicativos UWP
description: Saiba mais sobre o suporte do Visual Studio para testes de unidade Plataforma Universal do Windows aplicativos. O Visual Studio fornece modelos de teste de unidade para C#, Visual Basic e C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: fcf93dff859e2332c79b50086d0dc50d6bd304c8
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598335"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Passo a passo: Criar e executar testes de unidade para aplicativos UWP

O Visual Studio dá suporte para realizar testes de unidade em aplicativos da UWP (Plataforma Universal do Windows). O Visual Studio fornece modelos de projeto de teste de unidade para C#, Visual Basic e C++.

> [!TIP]
> Para obter mais informações sobre como desenvolver aplicativos da UWP, consulte [Introdução aos aplicativos UWP](/windows/uwp/get-started/).

Os procedimentos a seguir descrevem as etapas para criar, executar e depurar testes de unidade para um aplicativo UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Criar um projeto de teste de unidade para um aplicativo da UWP

::: moniker range=">=vs-2019"

1. Abra o Visual Studio. Na janela iniciar, escolha **criar um novo projeto**.

2. Na caixa de pesquisa da página **criar um novo projeto** , insira o **teste de unidade**.

   A lista de modelos filtra para os testes de unidade.

3. Selecione o modelo de **aplicativo de teste de unidade (universal do Windows)** para o C# ou Visual Basic e, em seguida, selecione **Avançar**.

   ![Criar novo aplicativo de teste de unidade UWP no Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Opcionalmente, altere o nome do projeto ou da solução e o local e, em seguida, selecione **criar**.

5. Opcionalmente, altere o destino e as versões de plataforma mínimas e, em seguida, selecione **OK**.

Depois de concluir essas etapas, o projeto de teste de unidade é criado e exibido no Gerenciador de Soluções.

![Projeto de teste de unidade UWP no Gerenciador de Soluções](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. No menu **Arquivo**, escolha **Novo**.

   A caixa de diálogo **Novo Projeto** é exibida.

2. Em Modelos, escolha a linguagem de programação com a qual você quer criar os testes de unidade e escolha a biblioteca de testes de unidade associada da Plataforma Universal do Windows. Por exemplo, escolha **Visual C#**, depois escolha **Windows Universal** e, em seguida, escolha **Biblioteca de Teste de Unidade (Universal Windows)**.

3. (Opcional) Na caixa de texto **Nome**, digite o nome que você quer usar para o projeto.

4. (Opcional) Modifique o caminho em que você deseja criar o projeto inserindo-o na caixa de texto **Local** ou escolhendo o botão **Procurar**.

5. (Opcional) Na caixa de texto **Nome da solução**, insira o nome que você deseja usar para sua solução.

6. Deixe a opção **Criar diretório para solução** selecionada e escolha o botão **OK**.

   ![Biblioteca de teste de unidade adaptada](../test/media/unit_test_win8_1.png)

   **Gerenciador de soluções** é populado com o projeto de teste de unidade UWP e o editor de código exibe o teste de unidade padrão intitulado UnitTest1.

   ![Novo projeto de teste de unidade adaptado](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Editar o arquivo de manifesto do aplicativo da UWP do projeto de teste de unidade

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo *Package. Appxmanifest* e escolha **abrir**.

2. No **Designer de Manifesto**, escolha a guia **Funcionalidades**.

3. Na lista em **Funcionalidades**, selecione as funcionalidades que seu teste de unidade e o código testado precisam. Por exemplo, marque a caixa de seleção **Internet** se o teste de unidade precisar e se o código testado precisar ter a capacidade de acessar a internet.

   > [!NOTE]
   > As funcionalidades selecionadas devem incluir somente o necessário para o funcionamento correto do teste de unidade.

   ![Manifesto do teste de unidade](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Codificar o teste de unidade para um aplicativo UWP

No editor de código, edite o teste de unidade e adicione as declarações e a lógica necessárias para seu teste.

## <a name="run-unit-tests"></a>Executar testes de unidade

Para compilar a solução e executar o teste de unidade usando o Gerenciador de testes:

1. No menu **Teste**, escolha **Windows** e **Gerenciador de Testes**.

2. No menu **Compilar** , escolha **Compilar solução**.

   O teste de unidade agora é mostrado no Gerenciador de testes.

   > [!NOTE]
   > Você deve compilar a solução para atualizar a lista de testes de unidade no Gerenciador de Testes.

3. No **Gerenciador de Testes**, escolha o teste de unidade criado.

4. Escolha **Executar Todos**.

   ![Gerenciador de Testes de Unidade &#45; executar teste de unidade](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Você pode selecionar um ou mais testes de unidade listados no Gerenciador de testes e clicar com o botão direito do mouse e escolher **executar testes selecionados**.
   >
   > Além disso, você pode optar por **Depurar os Testes Selecionados**, **Abrir Teste** e usar a opção **Propriedades**.
   >
   > ![Menu de contexto de teste de unidade de &#45; do Gerenciador de testes de unidade](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   O teste de unidade é executado. Após a conclusão, o Gerenciador de testes exibirá o status do teste e o tempo decorrido e fornecerá um link para a origem.

   ![Gerenciador de Testes de Unidade &#45; teste concluído](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Confira também

- [Testar aplicativos UWP com o Visual Studio](../test/unit-test-your-code.md)
- [Compilar e testar um aplicativo da UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
