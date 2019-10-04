---
title: Teste de unidade do código Python
description: A configuração do teste de unidade para o código Python no Visual Studio aproveita ao máximo as funcionalidades do Gerenciador de Testes para descobrir, executar e depurar testes.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933470"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Selecione a estrutura de teste para um projeto Python

O Visual Studio dá suporte a duas estruturas de teste para Python, [UnitTest](https://docs.python.org/3/library/unittest.html) e [pytest](https://pytest.org/en/latest/) (disponível no Visual Studio 2019 a partir da versão 16,3). Por padrão, nenhuma estrutura é selecionada quando você cria um projeto Python. Para especificar uma estrutura, clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e selecione a opção **Propriedades** . Isso abre o designer de projeto, que permite que você configure testes por meio da guia **teste** . Nessa guia, você pode selecionar a estrutura de teste que deseja usar para seu projeto. 

* Para a estrutura **UnitTest** , o diretório raiz do projeto é usado para a descoberta de teste. Esse local, bem como o padrão de texto para identificar os testes, podem ser modificados na guia **teste** para valores especificados pelo usuário.
* Para a estrutura **pytest** , as opções de teste, como local de teste e padrões de nome de arquivo, são especificadas usando o arquivo de configuração padrão pytest. ini. Consulte a [documentação de referência do pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) para obter mais detalhes.

Depois de salvar as configurações e a seleção da estrutura, a descoberta de testes será iniciada no Gerenciador de testes. Se a janela Gerenciador de testes ainda não estiver aberta, navegue até a barra de ferramentas e selecione **testar** > **Gerenciador de testes**.

## <a name="configure-testing-for-python-without-a-project"></a>Configurar testes para Python sem um projeto
O Visual Studio permite executar e testar o código Python existente sem um projeto, [abrindo uma pasta](../../quickstart-05-python-visual-studio-open-folder.md) com código Python. Sob essas circunstâncias, você precisará usar um arquivo **PythonSettings. JSON** para configurar o teste. 
1. Abra o código Python existente usando a opção **abrir uma pasta local** . 

   ![A tela de inicialização do Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Na janela Gerenciador de Soluções, clique no ícone **Mostrar todos os arquivos** para mostrar todos os arquivos na pasta atual.

   ![Botão Mostrar todos os arquivos](../../media/unit-test-show-files.png)

1. Navegue até o arquivo **PythonSettings. JSON** na pasta **configurações locais** . Se você não vir esse arquivo na pasta **configurações locais** , crie-o manualmente.
   
1. Adicione o campo **TestFrameWork** ao arquivo de configurações e defina-o como **pytest** ou **UnitTest** dependendo da estrutura de teste que você deseja usar.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Para a estrutura **UnitTest** , se os campos **UnitTestRootDirectory** e **UnitTestPattern** não forem especificados no arquivo PythonSettings. JSON, eles serão adicionados e atribuídos valores padrão "." e "Test *. py", respectivamente.

1. Se a sua pasta contiver um diretório **src** separado da pasta que contém seus testes, especifique o caminho para a pasta **src** usando o campo **SearchPaths** em seu arquivo **PythonSettings. JSON** .

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Salve as alterações no arquivo PythonSettings. JSON para iniciar a descoberta de teste para a estrutura especificada. 
   > [!Note]
   > Se a janela Test Explorer já estiver aberta, **CTRL** + **R, uma** também disparará A descoberta.

## <a name="discover-and-view-tests"></a>Descobrir e exibir testes

Por padrão, o Visual Studio identifica os testes **UnitTest** e **pytest** como métodos cujos nomes começam com `test`. Para ver a descoberta de teste, faça o seguinte:

1. Abra um [projeto do Python](../../managing-python-projects-in-visual-studio.md).

1. Depois que o projeto for carregado no Visual Studio, clique com o botão direito do mouse em seu projeto no Gerenciador de Soluções e selecione a estrutura **UnitTest** ou **Pytest** na guia **teste** de propriedades.
   > [!Note]
   > Se você usar a estrutura pytest, poderá especificar o local de teste e os padrões de nome de arquivo usando o arquivo de configuração padrão pytest. ini. Por padrão, a pasta de trabalho/projeto é usada, com um padrão de `test_*py` e `*_test.py`. Consulte a [documentação de referência do pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) para obter mais detalhes.

1. Depois que a estrutura for selecionada, clique com o botão direito do mouse no projeto novamente e selecione **adicionar** > **novo item**, em seguida, selecione **teste de unidade do python** seguido por **Adicionar**.

1. Essa ação cria um arquivo *test_1. py* com código que importa o módulo `unittest` padrão, deriva uma classe de teste de `unittest.TestCase` e invoca `unittest.main()` se você executar o script diretamente:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Salve o arquivo, se necessário, abra o **Gerenciador de testes** com o comando de menu **Test** > **Test Explorer** .

1. O **Gerenciador de Testes** pesquisa os testes no projeto e os exibe conforme mostrado abaixo. Se você clicar duas vezes em um teste, seu arquivo de origem será aberto.

    ![Gerenciador de Testes mostrando o test_A padrão](../../media/unit-test-a-2.png) 

1. Conforme você adiciona mais testes ao seu projeto, pode organizar o modo de exibição no **Gerenciador de testes** usando o menu **Agrupar por** na barra de ferramentas:

    ![Menu da barra de ferramentas Agrupar Por do Gerenciador de Testes](../../media/unit-test-group-menu-2.png) 

1. Também é possível inserir um texto no campo **Pesquisar** para filtrar os testes por nome.

Para obter mais informações sobre o módulo `unittest` e sobre como escrever testes, consulte a [documentação do python 2,7](https://docs.python.org/2/library/unittest.html) ou a [documentação do python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Executar testes

No **Gerenciador de Testes**, é possível executar testes de várias maneiras:

- **Executar Todos** claramente executa todos os testes mostrados (sujeito a filtros).
- O menu **Executar** fornece comandos para executar testes com falha, aprovados ou não executados como um grupo.
- É possível selecionar um ou mais testes, clicar com o botão direito do mouse e selecionar **Executar Testes Selecionados**.

Os testes são executados em segundo plano e o **Gerenciador de Testes** atualiza o status de cada teste conforme ele é concluído:

- Os testes aprovados mostram um tique verde e o tempo necessário para executar o teste:

    ![Status do test_A aprovado](../../media/unit-test-A-pass.png)

- Os testes com falha mostram uma cruz vermelha com um link **Saída** que mostra a saída do console e a saída `unittest` da execução de teste:

    ![Status do test_A com falha](../../media/unit-test-A-fail.png)

    ![test_A com falha com motivo](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Depurar testes

Como os testes de unidade são partes do código, eles estão sujeitos a bugs, assim como qualquer outro código e, ocasionalmente, precisam ser executados em um depurador. No depurador é possível definir pontos de interrupção, examinar variáveis e executar o código em etapas. O Visual Studio também fornece ferramentas de diagnóstico para testes de unidade.

> [!Note]
> Por padrão, a depuração de teste usa o depurador ptvsd 4. Se você quiser usar o ptvsd 3, poderá selecionar a opção **usar depurador herdado** em **ferramentas** > **opções** > **Python** > **Debugging**. 

Para iniciar a depuração, defina um ponto de interrupção inicial no código, clique com o botão direito do mouse no teste (ou em uma seleção) no **Gerenciador de Testes** e escolha **Depurar Testes Selecionados**. O Visual Studio inicia o depurador do Python como faria com o código do aplicativo.

![Depurando um teste](../../media/unit-test-debugging.png)

Você também pode usar a **cobertura de código de análise para testes selecionados**. Para obter mais informações, confira [Usar a cobertura de código para determinar quanto do código está sendo testado](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
