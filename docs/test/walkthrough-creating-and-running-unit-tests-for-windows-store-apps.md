---
title: Criando e executando testes de unidade para aplicativos UWP
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
ms.openlocfilehash: 4109f743caf7c62450591f78e90b92113fc4107e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568874"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Passo a passo: criar e executar testes de unidade para aplicativos UWP

O Visual Studio dá suporte para realizar testes de unidade em aplicativos da UWP (Plataforma Universal do Windows). O Visual Studio fornece modelos de projeto de teste unitário para C#, Visual Basic e C++.

> [!TIP]
> Para obter mais informações sobre como desenvolver aplicativos da UWP, consulte [Introdução aos aplicativos UWP](/windows/uwp/get-started/).

Os procedimentos a seguir descrevem as etapas para criar, executar e depurar testes de unidade para um aplicativo UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Criar um projeto de teste de unidade para um aplicativo da UWP

::: moniker range=">=vs-2019"

1. Abra o Visual Studio. Na janela inicial, escolha **Criar um novo projeto**.

2. Na caixa de pesquisa da Criar uma nova página **de projeto,** insira **o teste da unidade**.

   A lista de modelos filtra para aqueles para testes unitários.

3. Selecione o modelo **do Aplicativo de Teste de Unidade (Universal Windows)** para C# ou Visual Basic e, em seguida, selecione **Next**.

   ![Crie novo aplicativo de teste de unidade UWP no Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Alterar opcionalmente o nome e o local do projeto ou da solução e, em seguida, selecionar **Criar**.

5. Opcionalmente altere as versões de destino e plataforma mínima e selecione **OK**.

Após concluir essas etapas, o projeto de teste da unidade é criado e exibido no Solution Explorer.

![Projeto de teste de unidade UWP no Solution Explorer](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

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

   **O Solution Explorer** está preenchido com o projeto de teste da unidade UWP, e o editor de código exibe o teste padrão da unidade intitulado UnitTest1.

   ![Novo projeto de teste de unidade adaptado](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Editar o arquivo de manifesto do aplicativo da UWP do projeto de teste de unidade

1. No **Solution Explorer,** clique com o botão direito do mouse no arquivo *Package.appxmanifest* e escolha **Abrir**.

2. No **Designer de Manifesto**, escolha a guia **Funcionalidades**.

3. Na lista em **Funcionalidades**, selecione as funcionalidades que seu teste de unidade e o código testado precisam. Por exemplo, marque a caixa de seleção **Internet** se o teste de unidade precisar e se o código testado precisar ter a capacidade de acessar a internet.

   > [!NOTE]
   > As funcionalidades selecionadas devem incluir somente o necessário para o funcionamento correto do teste de unidade.

   ![Manifesto do teste de unidade](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Codificar o teste de unidade para um aplicativo UWP

No editor de código, edite o teste da unidade e adicione as afirmações e a lógica necessárias para o teste.

## <a name="run-unit-tests"></a>Executar testes de unidade

Para construir a solução e executar o teste da unidade usando o Test Explorer:

1. No menu **Teste**, escolha **Windows** e **Gerenciador de Testes**.

2. No menu **Build,** escolha **Build Solution**.

   Seu teste unitário agora é mostrado no Test Explorer.

   > [!NOTE]
   > Você deve compilar a solução para atualizar a lista de testes de unidade no Gerenciador de Testes.

3. No **Gerenciador de Testes**, escolha o teste de unidade criado.

4. Escolha **Executar Todos**.

   ![Gerenciador de Testes de Unidade &#45; executar teste de unidade](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Você pode selecionar um ou mais testes de unidade listados no Test Explorer e, em seguida, clicar com o botão direito do mouse e selecionar **Executar testes selecionados**.
   >
   > Além disso, você pode optar por **Depurar os Testes Selecionados**, **Abrir Teste**e usar a opção **Propriedades**.
   >
   > ![Menu de contexto de teste da unidade do &#45; do Unit Test Explorer](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   O teste de unidade é executado. Após a conclusão, o Test Explorer exibe o status do teste e o tempo decorrido e fornece um link para a fonte.

   ![Gerenciador de Testes de Unidade &#45; teste concluído](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Confira também

- [Testar aplicativos UWP com o Visual Studio](../test/unit-test-your-code.md)
- [Compilar e testar um aplicativo da UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
